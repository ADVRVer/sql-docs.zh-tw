---
title: "建立同義字 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_SYNONYM_TSQL
- SYNONYM_TSQL
- SYNONYM
- CREATE SYNONYM
dev_langs:
- TSQL
helpviewer_keywords:
- alternate names [SQL Server]
- names [SQL Server], synonyms
- CREATE SYNONYM statement
- synonyms [SQL Server], creating
ms.assetid: 41313809-e970-449c-bc35-85da2ef96e48
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 065b00489ac2ccd0c86e67719679a0b9cc0ece1b
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="create-synonym-transact-sql"></a>CREATE SYNONYM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  建立新的同義字。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
-- SQL Server Syntax  
  
CREATE SYNONYM [ schema_name_1. ] synonym_name FOR <object>  
  
<object> :: =  
{  
    [ server_name.[ database_name ] . [ schema_name_2 ]. object_name   
  | database_name . [ schema_name_2 ].| schema_name_2. ] object_name  
}  
```  
  
```  
-- Azure SQL Database Syntax  
  
CREATE SYNONYM [ schema_name_1. ] synonym_name FOR < object >  
  
< object > :: =  
{  
    [database_name. [ schema_name_2 ].| schema_name_2. ] object_name  
}  
```  
  
## <a name="arguments"></a>引數  
 *schema_name_1*  
 指定建立同義字的結構描述。 如果*結構描述*未指定，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]會使用目前使用者的預設結構描述。  
  
 *synonym_name*  
 這是新同義字的名稱。  
  
 *伺服器名稱*  
 **適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 這是基底物件所在的伺服器名稱。  
  
 *database_name*  
 這是基底物件所在的資料庫名稱。 如果*database_name*未指定，會使用目前的資料庫名稱。  
  
 *schema_name_2*  
 這是基底物件的結構描述名稱。 如果*schema_name*未指定使用目前使用者的預設結構描述。  
  
 *object_name*  
 這是同義字參考的基底物件名稱。  
  
 當 database_name 是目前的資料庫或 database_name 是 tempdb，而且 object_name 開頭為 # 時，Windows Azure SQL Database 支援三部分名稱格式 database_name.[schema_name].object_name。  
  
## <a name="remarks"></a>備註  
 在建立同義字時，基底物件不需要存在。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會在執行階段檢查基底物件是否存在。  
  
 您可以建立下列物件類型的同義字：  
  
|||  
|-|-|  
|組件 (CLR) 預存程序|組件 (CLR) 資料表值函式|  
|組件 (CLR) 純量函數|組件彙總 (CLR) 彙總函式|  
|複寫篩選程序|擴充預存程序|  
|SQL 純量函數|SQL 資料表值函式|  
|SQL 嵌入資料表值函式|SQL 預存程序|  
|檢視|資料表<sup>1</sup> （使用者定義）|  
  
 <sup>1 包括本機和全域暫存資料表</sup>  
  
 不支援函數基底物件的四部份名稱。  
  
 動態 SQL 中的同義字可以建立、卸除和參考。  
  
## <a name="permissions"></a>Permissions  
 若要以給定結構描述建立同義字，使用者必須擁有 CREATE SYNONYM 權限，並擁有該結構描述或 ALTER SCHEMA 權限。  
  
 CREATE SYNONYM 權限是可授與的權限。  
  
> [!NOTE]  
>  您不需要基底物件的權限，便能夠成功編譯 CREATE SYNONYM 陳述式，因為基底物件的所有權限檢查都會延遲到執行階段。  
  
## <a name="examples"></a>範例  
  
### <a name="a-creating-a-synonym-for-a-local-object"></a>A. 建立本機物件的同義字  
 下列範例會先建立 `Product` 資料庫中之基底物件 `AdventureWorks2012` 的同義字，再查詢這個同義字。  
  
```  
-- Create a synonym for the Product table in AdventureWorks2012.  
CREATE SYNONYM MyProduct  
FOR AdventureWorks2012.Production.Product;  
GO  
  
-- Query the Product table by using the synonym.  
SELECT ProductID, Name   
FROM MyProduct  
WHERE ProductID < 5;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ----------------------- 
 ProductID   Name 
 ----------- -------------------------- 
 1           Adjustable Race 
 2           Bearing Ball 
 3           BB Ball Bearing 
 4           Headset Ball Bearings 

 (4 row(s) affected)
``` 
  
### <a name="b-creating-a-synonym-to-remote-object"></a>B. 建立遠端物件的同義字  
 在下列範例中，基底物件 `Contact` 在名稱為 `Server_Remote` 的遠端伺服器中。  
  
**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
```  
EXEC sp_addlinkedserver Server_Remote;  
GO  
USE tempdb;  
GO  
CREATE SYNONYM MyEmployee FOR Server_Remote.AdventureWorks2012.HumanResources.Employee;  
GO  
```  
  
### <a name="c-creating-a-synonym-for-a-user-defined-function"></a>C. 建立使用者定義函數的同義字  
 下列範例會建立名為 `dbo.OrderDozen` 的函數，以便將訂單數量增加為平均一打的單位。 然後，此範例會建立 `dbo.CorrectOrder` 函數的同義字 `dbo.OrderDozen`。  
  
```  
-- Creating the dbo.OrderDozen function  
CREATE FUNCTION dbo.OrderDozen (@OrderAmt int)  
RETURNS int  
WITH EXECUTE AS CALLER  
AS  
BEGIN  
IF @OrderAmt % 12 <> 0  
BEGIN  
    SET @OrderAmt +=  12 - (@OrderAmt % 12)  
END  
RETURN(@OrderAmt);  
END;  
GO  
  
-- Using the dbo.OrderDozen function  
DECLARE @Amt int;  
SET @Amt = 15;  
SELECT @Amt AS OriginalOrder, dbo.OrderDozen(@Amt) AS ModifiedOrder;  
  
-- Create a synonym dbo.CorrectOrder for the dbo.OrderDozen function.  
CREATE SYNONYM dbo.CorrectOrder  
FOR dbo.OrderDozen;  
GO  
  
-- Using the dbo.CorrectOrder synonym.  
DECLARE @Amt int;  
SET @Amt = 15;  
SELECT @Amt AS OriginalOrder, dbo.CorrectOrder(@Amt) AS ModifiedOrder;  
```  
  
## <a name="see-also"></a>另請參閱  
 [卸除同義字 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/drop-synonym-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

