---
title: sys.fn_listextendedproperty (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_listextendedproperty
- fn_listextendedproperty_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_listextendedproperty function
- displaying extended properties
- database extended properties [SQL Server]
- viewing extended properties
- column extended properties [SQL Server]
- sys.fn_listextendedproperties function
- database objects [SQL Server], extended properties
- extended properties [SQL Server], columns
- table extended properties [SQL Server]
ms.assetid: 59bbb91f-a277-4a35-803e-dcb91e847a49
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d37331a3e9262c9c86afa95a432fdfc422ae6688
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43105078"
---
# <a name="sysfnlistextendedproperty-transact-sql"></a>sys.fn_listextendedproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回資料庫物件的擴充屬性值。  
 
 
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
fn_listextendedproperty (   
    { default | 'property_name' | NULL }   
  , { default | 'level0_object_type' | NULL }   
  , { default | 'level0_object_name' | NULL }   
  , { default | 'level1_object_type' | NULL }   
  , { default | 'level1_object_name' | NULL }   
  , { default | 'level2_object_type' | NULL }   
  , { default | 'level2_object_name' | NULL }   
  )   
```  
  
## <a name="arguments"></a>引數  
 {預設 |'*property_name*' |NULL}  
 屬性的名稱。 *property_name*已**sysname**。 有效的輸入是預設值、NULL 或屬性名稱。  
  
 {預設 |'*level0_object_type&lt*' |NULL}  
 使用者或使用者定義類型。 *level0_object_type&lt*已**varchar(128)**，預設值是 NULL。 有效輸入如下：ASSEMBLY、CONTRACT、EVENT NOTIFICATION、FILEGROUP、MESSAGE TYPE、PARTITION FUNCTION、PARTITION SCHEME、REMOTE SERVICE BINDING、ROUTE、SCHEMA、SERVICE、TRIGGER、TYPE、USER 和 NULL。  
  
> [!IMPORTANT]  
>  在未來的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本中，會移除層級 0 類型的 USER 和 TYPE。 請避免在新的開發工作中使用這些功能，並規劃修改目前使用這些功能的應用程式。 請改用 SCHEMA 來當做層級 0 類型，而不是使用 USER。 如果是 TYPE，請使用 SCHEMA 當做層級 0 類型，並使用 TYPE 當做層級 1 類型。  
  
 {預設 |'*level0_object_name&lt*' |NULL}  
 這是所指定之層級 0 物件類型的名稱。 *level0_object_name&lt*已**sysname**預設值是 NULL。 有效的輸入是預設值、NULL 或物件名稱。  
  
 {預設 |'*level1_object_type&lt*' |NULL}  
 這是層級 1 物件的類型。 *level1_object_type&lt*已**varchar(128)** 預設值是 NULL。 有效輸入如下：AGGREGATE、DEFAULT、FUNCTION、LOGICAL FILE NAME、PROCEDURE、QUEUE、RULE、SYNONYM、TABLE、TYPE、VIEW、XML SCHEMA COLLECTION 和 NULL。  
  
> [!NOTE]  
>  預設值對應到 NULL，'default' 對應到物件類型 DEFAULT。  
  
 {預設 |'*level1_object_name&lt*' |NULL}  
 這是所指定之層級 1 物件類型的名稱。 *level1_object_name&lt*已**sysname**預設值是 NULL。 有效的輸入是預設值、NULL 或物件名稱。  
  
 {預設 |'*level2_object_type&lt*' |NULL}  
 這是層級 2 物件的類型。 *level2_object_type&lt*已**varchar(128)** 預設值是 NULL。 有效輸入有 DEFAULT、預設值 (對應到 NULL) 和 NULL。 有效的輸入，如*level2_object_type&lt*是資料行、 條件約束、 EVENT NOTIFICATION、 索引、 參數、 觸發程序和 NULL。  
  
 {預設 |'*level2_object_name&lt*' |NULL}  
 這是所指定之層級 2 物件類型的名稱。 *level2_object_name&lt*已**sysname**預設值是 NULL。 有效的輸入是預設值、NULL 或物件名稱。  
  
## <a name="tables-returned"></a>傳回的資料表  
 這是 fn_listextendedproperty 傳回之資料表的格式。  
  
|資料行名稱|資料類型|  
|-----------------|---------------|  
|objtype|**sysname**|  
|objname|**sysname**|  
|NAME|**sysname**|  
|value|**sql_variant**|  
  
 如果傳回的資料表是空的，可能是物件沒有擴充屬性，也可能是使用者沒有列出物件擴充屬性的權限。 傳回資料庫本身的擴充屬性時，objtype 和 objname 資料行將為 NULL。  
  
## <a name="remarks"></a>備註  
 如果值*property_name*為 NULL 或預設值，fn_listextendedproperty 會傳回指定之物件的所有屬性。  
  
 當指定了物件類型，且對應物件名稱的值是 NULL 或預設值時，fn_listextendedproperty 會傳回指定類型之所有物件的所有擴充屬性。  
  
 物件會根據層級來區別，層級 0 是最高層級，層級 2 是最低層級。 如果指定了較低層級物件 (層級1 或層級 2) 的類型和名稱，就應該提供非 NULL 或預設值的父物件類型和名稱值。 否則，這個函數會傳回空的結果集。  
  
 **objname**固定為 Latin1_General_CI_AI。 不過您可以因應措施這藉由覆寫中比較的定序。  
  
```  
SELECT o.[object_id] AS 'table_id', o.[name] 'table_name',  
0 AS 'column_order', NULL AS 'column_name', NULL AS 'column_datatype',  
NULL AS 'column_length', Cast(e.value AS varchar(500)) AS 'column_description'  
FROM AdventureWorks.sys.objects AS o  
LEFT JOIN sys.fn_listextendedproperty(N'MS_Description', N'user',N'HumanResources',N'table', N'Employee', null, default) AS e  
    ON o.name = e.objname COLLATE SQL_Latin1_General_CP1_CI_AS  
WHERE o.name = 'Employee';  
```  
  
## <a name="permissions"></a>Permissions  
 列出物件擴充屬性的權限會隨著物件類型而不同。  
  
## <a name="examples"></a>範例  
  
### <a name="a-displaying-extended-properties-on-a-database"></a>A. 顯示資料庫的擴充屬性  
 下列範例會顯示資料庫物件本身所設定的所有擴充屬性。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT objtype, objname, name, value  
FROM fn_listextendedproperty(default, default, default, default, default, default, default);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `objtype    objname     name            value`  
  
 `---------  ---------   -----------     ----------------------------`  
  
 `NULL       NULL        MS_Description  AdventureWorks2008 Sample OLTP Database`  
  
 `(1 row(s) affected)`  
  
### <a name="b-displaying-extended-properties-on-all-columns-in-a-table"></a>B. 顯示資料表中所有資料行的擴充屬性  
 下列範例會列出資料行中的擴充的屬性`ScrapReason`資料表。 這包含在 `Production` 結構描述中。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT objtype, objname, name, value  
FROM fn_listextendedproperty (NULL, 'schema', 'Production', 'table', 'ScrapReason', 'column', default);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `objtype objname      name            value`  
  
 `------- -----------  -------------   ------------------------`  
  
 `COLUMN ScrapReasonID MS_Description  Primary key for ScrapReason records.`  
  
 `COLUMN Name          MS_Description  Failure description.`  
  
 `COLUMN ModifiedDate  MS_Description  Date the record was last updated.`  
  
 `(3 row(s) affected)`  
  
### <a name="c-displaying-extended-properties-on-all-tables-in-a-schema"></a>C. 顯示結構描述中所有資料表的擴充屬性  
 下列範例會列出所有資料表中所包含的擴充的屬性`Sales`結構描述。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT objtype, objname, name, value  
FROM fn_listextendedproperty (NULL, 'schema', 'Sales', 'table', default, NULL, NULL);  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_addextendedproperty &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md)   
 [sp_dropextendedproperty &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproperty-transact-sql.md)   
 [sp_updateextendedproperty &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-updateextendedproperty-transact-sql.md)   
 [sys.extended_properties &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-catalog-views/extended-properties-catalog-views-sys-extended-properties.md)  
  
  
