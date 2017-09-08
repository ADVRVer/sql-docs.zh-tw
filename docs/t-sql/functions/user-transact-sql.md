---
title: "使用者 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- USER
- USER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- usernames [SQL Server]
- system-supplied usernames [SQL Server]
- USER function
- users [SQL Server], database names
- names [SQL Server], database users
- database usernames [SQL Server]
ms.assetid: 82bbbd94-870c-4c43-9ed9-d9abc767a6be
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5230769c1e41d5831d77c3711c9b5c4a215414cb
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="user-transact-sql"></a>USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  當未指定預設值時，允許將目前使用者之資料庫使用者名稱的系統提供值插入資料表。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
USER  
```  
  
## <a name="return-types"></a>傳回類型  
 **char**  
  
## <a name="remarks"></a>備註  
 USER 提供與 USER_NAME 系統函數相同的功能。  
  
 USER 在 CREATE TABLE 或 ALTER TABLE 陳述式中是搭配 DEFAULT 條件約束使用，或者作為標準函數使用。  
  
 USER 一律會傳回目前內容的名稱。 在 EXECUTE AS 陳述式之後呼叫 USER 時，USER 會傳回模擬內容的名稱。  
  
 如果 Windows 主體利用群組中的成員資格來存取資料庫，則 USER 會傳回 Windows 主體名稱而非群組名稱。  
  
## <a name="examples"></a>範例  
  
### <a name="a-using-user-to-return-the-database-user-name"></a>A. 使用 USER 傳回資料庫使用者名稱  
 下列範例宣告一個變數為 `char`、將 USER 的目前值指派給這個變數，然後列印這個變數與文字描述。  
  
```  
DECLARE @usr char(30)  
SET @usr = user  
SELECT 'The current user''s database username is: '+ @usr  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `-----------------------------------------------------------------------`  
  
 `The current user's database username is: dbo`  
  
 `(1 row(s) affected)`  
  
### <a name="b-using-user-with-default-constraints"></a>B. 搭配 DEFAULT 條件約束來使用 USER  
 下列範例會使用 `USER` 做為銷售資料列之銷售員的 `DEFAULT` 條件約束，來建立資料表。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE inventory22  
(  
 part_id int IDENTITY(100, 1) NOT NULL,  
 description varchar(30) NOT NULL,  
 entry_person varchar(30) NOT NULL DEFAULT USER   
)  
GO  
INSERT inventory22 (description)  
VALUES ('Red pencil')  
INSERT inventory22 (description)  
VALUES ('Blue pencil')  
INSERT inventory22 (description)  
VALUES ('Green pencil')  
INSERT inventory22 (description)  
VALUES ('Black pencil')  
INSERT inventory22 (description)  
VALUES ('Yellow pencil')  
GO  
```  
  
 下列查詢會選取 `inventory22` 資料表的所有資訊：  
  
```  
SELECT * FROM inventory22 ORDER BY part_id;  
GO  
```  
  
 結果集如下 (請注意 `entry-person` 的值)：  
  
 `part_id     description                    entry_person`  
  
 `----------- ------------------------------ -------------------------`  
  
 `100         Red pencil                     dbo`  
  
 `101         Blue pencil                    dbo`  
  
 `102         Green pencil                   dbo`  
  
 `103         Black pencil                   dbo`  
  
 `104         Yellow pencil                  dbo`  
  
 `(5 row(s) affected)`  
  
### <a name="c-using-user-in-combination-with-execute-as"></a>C. 與 EXECUTE AS 合併使用 USER  
 下列範例說明在模擬工作階段中進行呼叫時，`USER` 的行為。  
  
```  
SELECT USER;  
GO  
EXECUTE AS USER = 'Mario';  
GO  
SELECT USER;  
GO  
REVERT;  
GO  
SELECT USER;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DBO`  
  
 `Mario`  
  
 `DBO`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-user-to-return-the-database-user-name"></a>D. 使用 USER 傳回資料庫使用者名稱  
 下列範例宣告一個變數為 `char`、將 USER 的目前值指派給這個變數，然後列印這個變數與文字描述。  
  
```  
DECLARE @usr char(30)  
SET @usr = user  
SELECT 'The current user''s database username is: '+ @usr  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `-----------------------------------------------------------------------`  
  
 `The current user's database username is: dbo`  
  
 `(1 row(s) affected)`  
  
## <a name="see-also"></a>另請參閱  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CURRENT_TIMESTAMP &#40;TRANSACT-SQL &#41;](../../t-sql/functions/current-timestamp-transact-sql.md)   
 [CURRENT_USER &#40;TRANSACT-SQL &#41;](../../t-sql/functions/current-user-transact-sql.md)   
 [安全性函數 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [SESSION_USER &#40;TRANSACT-SQL &#41;](../../t-sql/functions/session-user-transact-sql.md)   
 [SYSTEM_USER &#40;TRANSACT-SQL &#41;](../../t-sql/functions/system-user-transact-sql.md)   
 [USER_NAME &#40;TRANSACT-SQL &#41;](../../t-sql/functions/user-name-transact-sql.md)  
  
  


