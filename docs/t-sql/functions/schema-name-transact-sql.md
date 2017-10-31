---
title: "C H (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SCHEMA_NAME
- SCHEMA_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SCHEMA_NAME function
- schemas [SQL Server], names
ms.assetid: 20071b77-2b6e-4ce7-a8e3-fa71480baf73
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: bbc8d08ff59f85544fe3f11712c6780431bc76d7
ms.contentlocale: zh-tw
ms.lasthandoff: 10/17/2017

---
# <a name="schemaname-transact-sql"></a>SCHEMA_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回與結構描述識別碼相關聯的結構描述名稱。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
SCHEMA_NAME ( [ schema_id ] )  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|----------|----------------|  
|*schema_id*|結構描述的識別碼。 *schema_id*是**int**。如果*schema_id*是未定義時，SCHEMA_NAME 會傳回呼叫端的預設結構描述名稱。|  
  
## <a name="return-types"></a>傳回類型  
 **sysname**  
  
 傳回 NULL *schema_id*不是有效的識別碼。  
  
## <a name="remarks"></a>備註  
 SCHEMA_NAME 會傳回系統結構描述和使用者自訂結構描述的名稱。 SCHEMA_NAME 可在選取清單、WHERE 子句及任何允許使用運算式的位置中呼叫。  
  
## <a name="examples"></a>範例  
  
### <a name="a-returning-the-name-of-the-default-schema-of-the-caller"></a>A. 傳回呼叫端預設結構描述的名稱  
  
```  
SELECT SCHEMA_NAME();  
```  
  
### <a name="b-returning-the-name-of-a-schema-by-using-an-id"></a>B. 使用識別碼來傳回結構描述的名稱  
  
```  
SELECT SCHEMA_NAME(1);  
```  
  
## <a name="see-also"></a>另請參閱  
 [運算式 &#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [SCHEMA_ID &#40;TRANSACT-SQL &#41;](../../t-sql/functions/schema-id-transact-sql.md)   
 [sys.schemas &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [中繼資料函數 &#40;TRANSACT-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [其中 &#40;TRANSACT-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  


