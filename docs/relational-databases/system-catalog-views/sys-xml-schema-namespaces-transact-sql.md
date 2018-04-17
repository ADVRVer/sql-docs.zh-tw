---
title: 'sys.xml_schema_namespaces: (TRANSACT-SQL) |Microsoft 文件'
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_namespaces_TSQL
- sys.xml_schema_namespaces
- xml_schema_namespaces
- xml_schema_namespaces_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_namespaces catalog view
ms.assetid: 3ed42dd6-929a-41de-80e8-d3a0a488bc7a
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1f5a0c499516ee4d4e652fc7c727aa3395a98c61
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sysxmlschemanamespaces-transact-sql"></a>sys.xml_schema_namespaces (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對每一個 XSD 定義的 XML 命名空間，各傳回一個資料列。 下列 tuple 是唯一： **collection_id**， **namespace_id**，和**collection_id**，和**名稱**。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**xml_collection_id**|**int**|含有這個命名空間的 XML 結構描述集合識別碼。|  
|**name**|**nvarchar(4000)**|XML 命名空間的名稱。 空白**名稱**表示沒有目標命名空間。|  
|**xml_namespace_id**|**int**|以 1 為基底的序數，可唯一識別資料庫的 XML 命名空間。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML 結構描述&#40;XML 類型系統&#41;目錄檢視&#40;Transact SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
