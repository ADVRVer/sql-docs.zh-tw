---
title: "@@PROCID (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@PROCID'
- '@@PROCID_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- stored procedures [SQL Server], identification numbers
- UDTs [SQL Server], object identifiers
- '@@PROCID function'
- user-defined functions [SQL Server], object identifiers
- triggers [SQL Server], object identifiers
- identification numbers [SQL Server], modules
- IDs [SQL Server], modules
- module object identifiers [SQL Server]
ms.assetid: 0d4882c7-edb8-49b1-a470-2c7497b8998f
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 99cb6e6d3615247544adec83ac2c292b936f9ee6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40procid-transact-sql"></a>&#x40;&#x40;PROCID (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回目前 [!INCLUDE[tsql](../../includes/tsql-md.md)] 模組的物件識別碼。 [!INCLUDE[tsql](../../includes/tsql-md.md)] 模組可能是預存程序、使用者自訂函數或觸發程序。 @@PROCID不能指定 CLR 模組或同處理序資料存取提供者。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
@@PROCID  
```  
  
## <a name="return-types"></a>傳回類型  
 **int**  
  
## <a name="examples"></a>範例  
 下列範例會利用 `@@PROCID` 做為 `OBJECT_NAME` 函數中的輸入參數，以在 `RAISERROR` 訊息中傳回預存程序的名稱。  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'usp_FindName', 'P' ) IS NOT NULL   
DROP PROCEDURE usp_FindName;  
GO  
CREATE PROCEDURE usp_FindName  
    @lastname varchar(40) = '%',   
    @firstname varchar(20) = '%'  
AS  
DECLARE @Count int;  
DECLARE @ProcName nvarchar(128);  
SELECT LastName, FirstName  
FROM Person.Person   
WHERE FirstName LIKE @firstname AND LastName LIKE @lastname;  
SET @Count = @@ROWCOUNT;  
SET @ProcName = OBJECT_NAME(@@PROCID);  
RAISERROR ('Stored procedure %s returned %d rows.', 16,10, @ProcName, @Count);  
GO  
EXECUTE dbo.usp_FindName 'P%', 'A%';  
```  
  
## <a name="see-also"></a>請參閱＜  
 [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)   
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [中繼資料函數 &#40;TRANSACT-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.objects &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [RAISERROR &#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
