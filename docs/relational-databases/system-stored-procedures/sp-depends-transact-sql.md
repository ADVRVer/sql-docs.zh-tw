---
title: sp_depends （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_depends
- sp_depends_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_depends
ms.assetid: d9934590-c6ae-4936-91c3-146055ef2c57
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9ee6b9df37e61dcb4eed45bc11431d49b160cf87
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053109"
---
# <a name="sp_depends-transact-sql"></a>sp_depends (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  顯示有關資料庫物件相依性的資訊，例如相依於資料表或檢視的檢視和程序，以及檢視或程序所相依的資料表或檢視。 不會報告對於目前資料庫外之物件的參考。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]請改用[sys.databases dm_sql_referencing_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)和[sys.databases。 dm_sql_referenced_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md) 。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_depends [ @objname = ] '<object>'   
  
<object> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name.  
    object_name  
}  
```  
  
## <a name="arguments"></a>引數  
 *database_name*  
 這是資料庫的名稱。  
  
 *schema_name*  
 這是物件所屬的結構描述名稱。  
  
 *object_name*  
 這是要檢查相依性的資料庫物件。 這個物件可能是資料表、檢視表、預存程序、使用者定義函數或觸發程序。 o*bject_name*是**Nvarchar （776）**，沒有預設值。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
 **sp_depends**會顯示兩個結果集。  
  
 下列結果集會顯示* \<物件>* 所相依的物件。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**Nvarchar （257** **）**|相依性存在的項目名稱。|  
|**type**|**Nvarchar （16）**|項目的類型。|  
|**已**|**Nvarchar （7）**|是否更新項目。|  
|**處於**|**Nvarchar （8）**|是否在 SELECT 陳述式中使用這個項目。|  
|**排**|**sysname**|存在相依性的資料行或參數。|  
  
 下列結果集會顯示相依于* \<物件>* 的物件。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**Nvarchar （257** **）**|相依性存在的項目名稱。|  
|**type**|**Nvarchar （16）**|項目的類型。|  
  
## <a name="permissions"></a>權限  
 需要 **public** 角色的成員資格。  
  
## <a name="examples"></a>範例  
  
### <a name="a-listing-dependencies-on-a-table"></a>A. 列出對於資料表的相依性  
 下列範例會列出相依於 `Sales.Customer` 資料庫中 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料表的資料庫物件。 指定了結構描述名稱和資料表名稱。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_depends @objname = N'Sales.Customer' ;  
```  
  
### <a name="b-listing-dependencies-on-a-trigger"></a>B. 列出對於觸發程序的相依性  
 下列範例列出 `iWorkOrder` 觸發程序相依的資料庫物件。  
  
```  
EXEC sp_depends @objname = N'AdventureWorks2012.Production.iWorkOrder' ;  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料庫引擎預存程式 &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sql_dependencies &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md)  
  
  
