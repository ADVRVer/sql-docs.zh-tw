---
title: sys.databases xml_indexes （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_indexes_TSQL
- xml_indexes_TSQL
- sys.xml_indexes
- xml_indexes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_indexes catalog view
ms.assetid: 3408de72-b067-4fda-b5d5-8e856dfd9db3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dc51d1c5113059fcf373005000105a8622d89e31
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824974"
---
# <a name="sysxml_indexes-transact-sql"></a>sys.xml_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對 XML 索引，各傳回一個資料列。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**\<繼承的資料行>**||從[sys.databases](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)繼承資料行。|  
|**using_xml_index_id**|**int**|NULL = 主要 XML 索引。<br /><br /> 非 Null = 次要 XML 索引。<br /><br /> 非 Null 是主要 XML 索引的自我聯結參考。|  
|**secondary_type**|**char （1）**|輸入次要索引的描述：<br /><br /> P = PATH 次要 XML 索引<br /><br /> V = VALUE 次要 XML 索引<br /><br /> R = PROPERTY 次要 XML 索引<br /><br /> NULL = 主要 XML 索引|  
|**secondary_type_desc**|**nvarchar(60)**|輸入次要索引的描述：<br /><br /> PATH = PATH 次要 XML 索引<br /><br /> VALUE = VALUE 次要 XML 索引<br /><br /> PROPERTY = PROPERTY 次要 XML 索引。<br /><br /> NULL = 主要 XML 索引|  
|**xml_index_type**|**tinyint**|索引類型：<br /><br /> 0 = 主要 XML 索引<br /><br /> 1 = 次要 XML 索引<br /><br /> 2 = 選擇性 XML 索引<br /><br /> 3 = 次要選擇性 XML 索引|  
|**xml_index_type_description**|**nvarchar(60)**|索引類型的描述：<br /><br /> PRIMARY_XML<br /><br /> 次要 XML 索引<br /><br /> 選擇性 XML 索引<br /><br /> 次要選擇性 XML 索引|  
|**path_id**|**int**|除了次要選擇性 XML 索引以外，其他所有 XML 索引都為 NULL。<br /><br /> 否則，就是用來建置次要選擇性 XML 索引的升級路徑識別碼。 這個值與 sys.selective_xml_index_paths 系統檢視的 path_id 值相同。|  
  
## <a name="permissions"></a>權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的目錄檢視](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [物件目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
