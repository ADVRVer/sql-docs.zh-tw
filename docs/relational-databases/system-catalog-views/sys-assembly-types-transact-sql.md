---
title: sys.assembly_types (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- assembly_types
- sys.assembly_types
- sys.assembly_types_TSQL
- assembly_types_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assembly_types catalog view
ms.assetid: 35f0384f-7a6d-41b1-9461-f1406d68f317
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1f62185fc99512a966789f1b878b23f90264fba9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721276"
---
# <a name="sysassemblytypes-transact-sql"></a>sys.assembly_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  針對由 CLR 組件所定義的每個使用者定義型別，各包含一個資料列。 下列**sys.assembly_types**出現在繼承的資料行清單 (請參閱[sys.types &#40;-&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)) 之後**rule_object_id**。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|建立這個類型所依據的組件識別碼。|  
|**assembly_class**|**sysname**|定義這個類型的組件內的類別名稱。|  
|**is_binary_ordered**|**bit**|排列這個類型的位元組，相當於在該類型利用比較運算子來排序。|  
|**is_fixed_length**|**bit**|類型長度一律與 max_length 一樣。|  
|**prog_id**|**nvarchar(40)**|COM 所看到的類型 ProgID。|  
|**assembly_qualified_name**|**nvarchar(4000)**|組件限定的類型名稱。 這個名稱是採用適合傳遞到 Type.GetType() 的格式。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [純量類型目錄檢視&#40;Transact SQL&#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)  
  
  
