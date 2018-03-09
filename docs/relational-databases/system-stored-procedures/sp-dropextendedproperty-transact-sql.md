---
title: "sp_dropextendedproperty (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_dropextendedproperty_TSQL
- sp_dropextendedproperty
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropextendedproperty
ms.assetid: 4851865a-86ca-4823-991a-182dd1934075
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ed3a14354abb946bd072cf1f1b3da29a1667c0e2
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2017
---
# <a name="spdropextendedproperty-transact-sql"></a>sp_dropextendedproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  卸除現有的擴充屬性。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_dropextendedproperty   
    [ @name = ] { 'property_name' }  
      [ , [ @level0type = ] { 'level0_object_type' }   
        , [ @level0name = ] { 'level0_object_name' }   
            [ , [ @level1type = ] { 'level1_object_type' }   
              , [ @level1name = ] { 'level1_object_name' }   
                [ , [ @level2type = ] { 'level2_object_type' }   
                  , [ @level2name = ] { 'level2_object_name' }   
                ]   
            ]   
        ]   
    ]   
```  
  
## <a name="arguments"></a>引數  
 [ @name=] {'*property_name*'}  
 這是要卸除的屬性名稱。 *property_name*是**sysname**不能是 NULL。  
  
 [ @level0type=] {'*level0_object_type*'}  
 這是所指定之層級 0 物件類型的名稱。 *level0_object_type*是**varchar （128)**，預設值是 NULL。  
  
 有效輸入如下：ASSEMBLY、CONTRACT、EVENT NOTIFICATION、FILEGROUP、MESSAGE TYPE、PARTITION FUNCTION、PARTITION SCHEME、REMOTE SERVICE BINDING、ROUTE、SCHEMA、SERVICE、USER、TRIGGER、TYPE 和 NULL。  
  
> [!IMPORTANT]  
>  在未來的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本中，會移除層級 0 類型的 USER 和 TYPE。 請避免在新的開發工作中使用這些功能，並規劃修改目前使用這些功能的應用程式。 請改用 SCHEMA 來當做層級 0 類型，而不是使用 USER。 如果是 TYPE，請使用 SCHEMA 當做層級 0 類型，並使用 TYPE 當做層級 1 類型。  
  
 [ @level0name=] {'*level0_object_name*'}  
 這是所指定之層級 0 物件類型的名稱。 *level0_object_name*是**sysname**預設值是 NULL。  
  
 [ @level1type=] {'*level1_object_type*'}  
 這是層級 1 物件的類型。 *level1_object_type*是**varchar （128)**預設值是 NULL。 有效輸入如下：AGGREGATE、DEFAULT、FUNCTION、LOGICAL FILE NAME、PROCEDURE、QUEUE、RULE、SYNONYM、TABLE、TABLE_TYPE、TYPE、VIEW、XML SCHEMA COLLECTION 和 NULL。  
  
 [ @level1name=] {'*level1_object_name*'}  
 這是所指定之層級 1 物件類型的名稱。 *level1_object_name*是**sysname**預設值是 NULL。  
  
 [ @level2type=] {'*level2_object_type*'}  
 這是層級 2 物件的類型。 *level2_object_type*是**varchar （128)**預設值是 NULL。 有效輸入如下：COLUMN、CONSTRAINT、EVENT NOTIFICATION、INDEX、PARAMETER、TRIGGER 和 NULL。  
  
 [ @level2name=] {'*level2_object_name*'}  
 這是所指定之層級 2 物件類型的名稱。 *level2_object_name*是**sysname**預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>備註  
 為了指定擴充屬性，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中的物件會分類成 3 個層級 (0、1 和 2)。 層級 0 是最高層級，定義為資料庫範圍所包含的物件。 層級 1 物件包含在結構描述或使用者範圍中，層級 2 物件包含在層級 1 物件中。 任何這些層級的物件都可以定義擴充屬性。 參考一個層級中的物件時，必須以所有較高層級物件的類型和名稱來限定。  
  
 給定有效*property_name*會刪除此屬性之後，如果所有物件類型和名稱都都是 null，且有屬性存在於目前資料庫。 請參閱本主題稍後的範例 B。  
  
## <a name="permissions"></a>Permissions  
 db_owner 和 db_ddladmin 固定資料庫角色的成員可卸除任何物件的擴充屬性，但下列為例外狀況：db_ddladmin 不能將屬性加入至資料庫本身或加入至使用者或角色。  
  
 使用者可以卸除他們所擁有之物件或他們有 ALTER 或 CONTROL 權限之物件的擴充屬性。  
  
## <a name="examples"></a>範例  
  
### <a name="a-dropping-an-extended-property-on-a-column"></a>A. 卸除資料行的擴充屬性  
 下列範例會從 `caption` 結構描述所包含之 `id` 資料表中的資料行 `T1` 中移除 `dbo` 屬性。  
  
```  
CREATE TABLE T1 (id int , name char (20));  
GO  
EXEC sp_addextendedproperty   
     @name = 'caption'   
    ,@value = 'Employee ID'   
    ,@level0type = 'schema'   
    ,@level0name = dbo  
    ,@level1type = 'table'  
    ,@level1name = 'T1'  
    ,@level2type = 'column'  
    ,@level2name = id;  
GO  
EXEC sp_dropextendedproperty   
     @name = 'caption'   
    ,@level0type = 'schema'   
    ,@level0name = dbo  
    ,@level1type = 'table'  
    ,@level1name = 'T1'  
    ,@level2type = 'column'  
    ,@level2name = id;  
GO  
DROP TABLE T1;  
GO  
```  
  
### <a name="b-dropping-an-extended-property-on-a-database"></a>B. 卸除資料庫的擴充屬性  
 下列範例會移除名為的屬性`MS_Description`從[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]範例資料庫。 由於此屬性位於資料庫本身，因此未指定任何物件類型和名稱。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_dropextendedproperty   
@name = N'MS_Description';  
GO  
```  
  
## <a name="see-also"></a>請參閱  
 [Database Engine 預存程序 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sys.fn_listextendedproperty &#40;TRANSACT-SQL &#41;](../../relational-databases/system-functions/sys-fn-listextendedproperty-transact-sql.md)   
 [sp_addextendedproperty &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md)   
 [sp_updateextendedproperty &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-updateextendedproperty-transact-sql.md)   
 [sys.extended_properties &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/extended-properties-catalog-views-sys-extended-properties.md)  
  
  
