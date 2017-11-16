---
title: "以 FROM 或子查詢實作 UPDATE | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 11/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 138f5b0e-f8a4-400f-b581-8062aebc62b6
caps.latest.revision: "4"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 337a85dddb52869d8ec54d13bb8231164b98f4e8
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="implementing-update-with-from-or-subqueries"></a>以 FROM 或子查詢實作 UPDATE
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

原生編譯的 T-SQL 模組不支援在 UPDATE 陳述式中使用 FROM 子句和子查詢 (SELECT 中才支援)。 UPDATE 陳述式和 FROM 子句通常可用來根據資料表值參數 (TVP) 更新資料表中的資訊，或在 AFTER 觸發程序中更新資料表中的資料行。 

如需根據 TVP 的更新案例，請參閱 [在原生編譯的預存程序中實作 MERGE 功能](../../relational-databases/in-memory-oltp/implementing-merge-functionality-in-a-natively-compiled-stored-procedure.md)。 

下列範例說明觸發程序中所執行的更新 - 資料表的 LastUpdated 資料行已更新為目前的日期/時間 AFTER 更新。 因應措施使用內含識別欄位的資料表變數及 WHILE 迴圈，來逐一查看資料表變數中的資料列，並執行個別更新。
  
以下是原始 T-SQL UPDATE 陳述式：  
  
  
  
  
    UPDATE dbo.Table1  
        SET LastUpdated = SysDateTime()  
        FROM  
            dbo.Table1 t  
            JOIN Inserted i ON t.Id = i.Id;  
  
  
  

本節中的 T-SQL 程式碼範例示範提供良好效能的因應措施。 此因應措施是在原生編譯的觸發程序中實作。 請注意，此程式碼必須包含：  
  
- 名為 dbo.Type1 的類型，也就是記憶體最佳化資料表類型。  
- 觸發程序中的 WHILE 迴圈。  
  - 此迴圈會從 Inserted 一次擷取一個資料列。  
  
  
  

    DROP TABLE IF EXISTS dbo.Table1;  
    go  
    DROP TYPE IF EXISTS dbo.Type1;  
    go  
    -----------------------------  
    <a name="---table-and-table-type"></a>-- 資料表和資料表類型
    -----------------------------
  
    CREATE TABLE dbo.Table1  
    (  
        Id           INT        NOT NULL  PRIMARY KEY NONCLUSTERED,  
        Column2      INT        NOT NULL,  
        LastUpdated  DATETIME2  NOT NULL  DEFAULT (SYSDATETIME())  
    )  
        WITH (MEMORY_OPTIMIZED = ON);  
    go  
  
  
    CREATE TYPE dbo.Type1 AS TABLE  
    (  
        Id       INT NOT  NULL,  
        
        RowID    INT NOT  NULL  IDENTITY,  
        INDEX ix_RowID HASH (RowID) WITH (BUCKET_COUNT=1024)
    )   
        WITH (MEMORY_OPTIMIZED = ON);  
    go  
    ----------------------------- 
    <a name="---trigger-that-contains-the-workaround-for-update-with-from"></a>-- 包含 UPDATE 和 FROM 之因應措施的觸發程序 
    -----------------------------  
  
    CREATE TRIGGER dbo.tr_a_u_Table1  
        ON dbo.Table1  
        WITH NATIVE_COMPILATION, SCHEMABINDING  
        AFTER UPDATE  
    AS BEGIN ATOMIC WITH  
        (  
        TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
        LANGUAGE = N'us_english'  
        )  
        
      DECLARE @tabvar1 dbo.Type1;  
    
      INSERT @tabvar1 (Id)   
          SELECT Id FROM Inserted;  
    
      DECLARE  
          @i INT = 1,  @Id INT,  
          @max INT = SCOPE_IDENTITY();  
    
      ---- 執行迴圈作為因應措施以模擬資料指標。
    ---- 逐一查看記憶體最佳化資料表變數中的資料列  
      --- 並針對每個資料列執行更新。  
    
      WHILE @i <= @max  
      BEGIN  
          SELECT @Id = Id  
              FROM @tabvar1  
              WHERE RowID = @i;  
    
          UPDATE dbo.Table1  
              SET LastUpdated = SysDateTime()  
              WHERE Id = @Id;  
    
          SET @i += 1;  
      END  
    END  
    go  
    -----------------------------  
    <a name="---test-to-verify-functionality"></a>-- 測試以驗證功能
    -----------------------------  
  
    SET NOCOUNT ON;  
  
    INSERT dbo.Table1 (Id, Column2)  
        VALUES (1,9), (2,9), (3,600);  
    
    SELECT N'BEFORE-Update' AS [BEFORE-Update], *  
        FROM dbo.Table1  
        ORDER BY Id;  
  
    WAITFOR DELAY '00:00:01';  

    UPDATE dbo.Table1  
        SET   Column2 += 1  
        WHERE Column2 <= 99;  
  
    SELECT N'AFTER--Update' AS [AFTER--Update], *  
        FROM dbo.Table1  
        ORDER BY Id;  
    go  
    -----------------------------  
  
    /**** 實際輸出:  
  
    BEFORE-Update   Id   Column2   LastUpdated  
    BEFORE-Update   1       9      2016-04-20 21:18:42.8394659  
    BEFORE-Update   2       9      2016-04-20 21:18:42.8394659  
    BEFORE-Update   3     600      2016-04-20 21:18:42.8394659  
  
    AFTER--Update   Id   Column2   LastUpdated  
    AFTER--Update   1      10      2016-04-20 21:18:43.8529692  
    AFTER--Update   2      10      2016-04-20 21:18:43.8529692  
    AFTER--Update   3     600      2016-04-20 21:18:42.8394659  
    ****/  
  
  
  
