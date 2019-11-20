---
title: 改變原生編譯的 T-SQL 模組 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 010318a0-6807-47c3-8ecc-bb7cb60513f0
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6979d05d29b151a34edfe1c220c9d9a4d3046359
ms.sourcegitcommit: e37636c275002200cf7b1e7f731cec5709473913
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "73983013"
---
# <a name="altering-natively-compiled-t-sql-modules"></a>更改原生編譯的 T-SQL 模組
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 及更新版本) 和 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 中，您可以在原生編譯預存程序和其他原生編譯的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 模組 (如純量 UDF 和觸發程序) 上使用 `ALTER` 陳述式來執行 `ALTER` 作業。  
  
在原生編譯的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 模組上執行 `ALTER` 時，該模組會使用新的定義重新編譯。 進行重新編譯時，舊版的模組仍可繼續執行。 編譯完成之後，即會清空模組執行，並安裝新版的程序。 當您改變原生編譯的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 模組時，可以修改以下選項。  
  
-   參數  
-   EXECUTE AS  
-   TRANSACTION ISOLATION LEVEL  
-   LANGUAGE  
-   DATEFIRST  
-   DATEFORMAT  
-   DELAYED_DURABILITY  
  
> [!NOTE]  
> 原生編譯 [!INCLUDE[tsql](../../includes/tsql-md.md)] 模組無法轉換成非原生編譯的模組。 非原生編譯 T-SQL 模組無法轉換成原生編譯的模組。  
  
如需 `ALTER PROCEDURE` 功能和語法的詳細資訊，請參閱 [ALTER PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-procedure-transact-sql.md)。  
  
您可以在原生編譯 [!INCLUDE[tsql](../../includes/tsql-md.md)] 模組上執行 [sp_recompile](../../relational-databases/system-stored-procedures/sp-recompile-transact-sql.md)，下次執行時就會重新編譯模組。  
  
## <a name="example"></a>範例  
以下範例會建立記憶體最佳化的資料表 (T1)，以及選取所有 T1 資料行的原生編譯預存程序 (usp_1)。 然後，更改 usp_1 以移除 `EXECUTE AS` 子句，變更 `LANGUAGE`，且只從 T1 選取一個資料行 (C1)。  
  
```sql  
CREATE TABLE [dbo].[T1] (  
  [c1] [int] NOT NULL,  
  [c2] [float] NOT NULL,  
  CONSTRAINT [PK_T1] PRIMARY KEY NONCLUSTERED ([c1])  
  ) WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_AND_DATA )  
GO  
  
CREATE PROCEDURE [dbo].[usp_1]  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english'  
)  
   SELECT c1, c2 FROM dbo.T1  
END  
GO  
  
ALTER PROCEDURE [dbo].[usp_1]  
WITH NATIVE_COMPILATION, SCHEMABINDING  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'Dutch'  
)  
   SELECT c1 FROM dbo.T1  
END  
GO    
```   
  
## <a name="see-also"></a>另請參閱  
 [原生編譯的預存程序](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)    
