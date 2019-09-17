---
title: sensitivity_classifications （Transact-sql） |Microsoft Docs
ms.date: 03/25/2019
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.author: mibar
author: barmichal
f1_keywords:
- 'sys.sensitivity_classifications '
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sensitivity_classifications statement
- dropping labels
- drop labels
- removing labels
- remove labels
- classification [SQL]
- labels [SQL]
- information types
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: a9d14cd93b08c0094ad984a6469b433e0b266479
ms.sourcegitcommit: 77293fb1f303ccfd236db9c9041d2fb2f64bce42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929783"
---
# <a name="syssensitivity_classifications-transact-sql"></a>sensitivity_classifications （Transact-sql）
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

針對資料庫中的每個分類專案，各傳回一個資料列。

|資料行名稱|資料類型|描述|
|-----------------|---------------|-----------------|  
|**class**|**int**|識別分類所在專案的類別|  
|**class_desc**|**varchar(16)**|分類所在專案的類別描述|  
|**major_id**|**int**|分類所在專案的識別碼。 < br \>< br \>如果類別為0，major_id 一律為0。<br>如果 class 是 1、2 或 7，則 major_id 就是 object_id。|  
|**minor_id**|**int**|分類所在專案的次要識別碼，會根據其類別加以解讀。<br><br>如果 class = 1，minor_id 就是 column_id （如果是 column），否則就是0（如果是 object）。<br>如果 class = 2，minor_id 就是 parameter_id。<br>如果 class = 7，minor_id 就是 index_id。 |  
|**label**|**sysname**|指派給敏感度分類的標籤（人類可讀取）|  
|**label_id**|**sysname**|與標籤相關聯的識別碼，可供資訊保護系統（例如 Azure 資訊保護（AIP））使用|  
|**information_type**|**sysname**|指派給敏感度分類的資訊類型（人類可讀取）|  
|**information_type_id**|**sysname**|與資訊類型相關聯的識別碼，可供資訊保護系統（例如 Azure 資訊保護（AIP））使用|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>備註  

- 這個視圖可讓您看到資料庫的分類狀態。 它可以用來管理資料庫分類，以及產生報表。
- 目前僅支援資料庫資料行的分類。 隨後
    - **類別**-一律會有值1（表示資料行）
    - **class_desc** -一律會有值*OBJECT_OR_COLUMN*
    - **major_id** -代表包含已分類資料行之資料表的識別碼，對應于 sys.databases. all _objects. object_id
    - **minor_id** -代表分類所在的資料行識別碼，對應于 sys.databases. all _columns. column_id

## <a name="examples"></a>範例

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. 列出所有分類的資料行及其對應的分類

下列範例會傳回一個資料表，其中列出資料庫中每個分類資料行的資料表名稱、資料行名稱、標籤、標籤識別碼、資訊類型、資訊類型識別碼。

> [!NOTE]
> 標籤是 Azure SQL 資料倉儲的關鍵字。

```sql
SELECT
    SCHEMA_NAME(sys.all_objects.schema_id) as SchemaName,
    sys.all_objects.name AS [TableName], sys.all_columns.name As [ColumnName],
    [Label], [Label_ID], [Information_Type], [Information_Type_ID]
FROM
          sys.sensitivity_classifications
left join sys.all_objects on sys.sensitivity_classifications.major_id = sys.all_objects.object_id
left join sys.all_columns on sys.sensitivity_classifications.major_id = sys.all_columns.object_id
                         and sys.sensitivity_classifications.minor_id = sys.all_columns.column_id
```

## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  

## <a name="see-also"></a>另請參閱  

[ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[DROP SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[開始使用 SQL 資訊保護](https://aka.ms/sqlip)
