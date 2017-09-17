---
title: "IS_OBJECTSIGNED (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IS_OBJECTSIGNED
- IS_OBJECTSIGNED_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IS_OBJECTSIGNED function
ms.assetid: afbc4f7f-8266-4ee6-9802-14a2dbe69ef6
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e346fb803e18d9a43afe15984166985ff0a3e408
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="isobjectsigned-transact-sql"></a>IS_OBJECTSIGNED (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  指出物件是否由指定的憑證或非對稱金鑰所簽署。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
IS_OBJECTSIGNED (   
'OBJECT', @object_id, @class, @thumbprint  
  )   
```  
  
## <a name="arguments"></a>引數  
 **' OBJECT'**  
 安全性實體類別的類型。  
  
 *@object_id*  
 正在測試之物件的 object_id。 *@object_id*型別**int**。  
  
 *@class*  
 物件的類別：  
  
-   'certificate'  
  
-   'asymmetric key'  
  
 *@class*是**sysname**。  
  
 *@thumbprint*  
 物件的 SHA 指模。 *@thumbprint*型別**varbinary(32)**。  
  
## <a name="returned-types"></a>傳回的類型  
 **int**  
  
## <a name="remarks"></a>備註  
 IS_OBJECTSIGNED 會傳回下列值。  
  
|傳回值|Description|  
|------------------|-----------------|  
|NULL|物件未簽署，或物件不是有效。|  
|0|物件已簽署，但簽章無效。|  
|1|已簽署物件。|  
  
## <a name="permissions"></a>Permissions  
 需要憑證或非對稱金鑰的 VIEW DEFINITION。  
  
## <a name="examples"></a>範例  
  
### <a name="a-displaying-extended-properties-on-a-database"></a>A. 顯示資料庫的擴充屬性  
 下列範例會測試中的 spt_fallback_db 資料表**主要**資料庫由結構描述簽署憑證簽署。  
  
```  
USE master;  
-- Declare a variable to hold a thumbprint and an object name  
DECLARE @thumbprint varbinary(20), @objectname sysname;  
  
-- Populate the thumbprint variable with the thumbprint of   
-- the master database schema signing certificate  
SELECT @thumbprint = thumbprint   
FROM sys.certificates   
WHERE name LIKE '%SchemaSigningCertificate%';  
  
-- Populate the object name variable with a table name in master  
SELECT @objectname = 'spt_fallback_db';  
  
-- Query to see if the table is signed by the thumbprint  
SELECT @objectname AS [object name],  
IS_OBJECTSIGNED(  
'OBJECT', OBJECT_ID(@objectname), 'certificate', @thumbprint  
) AS [Is the object signed?] ;  
```  
  
## <a name="see-also"></a>另請參閱  
 [sys.fn_check_object_signatures &#40;TRANSACT-SQL &#41;](../../relational-databases/system-functions/sys-fn-check-object-signatures-transact-sql.md)  
  
  

