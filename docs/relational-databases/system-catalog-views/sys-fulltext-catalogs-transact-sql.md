---
title: sys.fulltext_catalogs (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fulltext_catalogs_TSQL
- sys.fulltext_catalogs
- fulltext_catalogs
- fulltext_catalogs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_catalogs catalog view
ms.assetid: cf1489ff-4819-41fa-a62a-4ed797a16207
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d4f6099b6f741dd5f0f29687cacc37e6cdfe6fb2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62465772"
---
# <a name="sysfulltextcatalogs-transact-sql"></a>sys.fulltext_catalogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對每個全文檢索目錄，各包含一個資料列。  
  
> [!NOTE]  
>  未來版本將移除下列資料行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **data_space_id**， **file_id**，和**路徑**。 請勿在新的開發工作中使用這些資料行，並且儘速修改目前使用任何一個資料行的應用程式。  
 
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|fulltext_catalog_id|**int**|全文檢索目錄的識別碼。 這在各個資料庫中的全文檢索目錄都是唯一的。|  
|NAME|**sysname**|目錄名稱。 在資料庫中，這是唯一的。|  
|路徑|**nvarchar(260)**|檔案系統中全文檢索目錄的目錄名稱。|  
|is_default|**bit**|預設全文檢索目錄。<br /><br /> True = 是預設值。<br /><br /> False = 不是預設值。|  
|is_accent_sensitivity_on|**bit**|目錄的區分腔調字設定。<br /><br /> True = 區分腔調字。<br /><br /> False = 不區分腔調字。|  
|data_space_id|**int**|建立這個目錄的檔案群組。|  
|file_id|**int**|與目錄相關聯之全文檢索檔案的檔案識別碼。|  
|principal_id|**int**|擁有全文檢索目錄的資料庫主體識別碼。|  
|is_importing|**bit**|指出是否正在匯入全文檢索目錄：<br /><br /> 1 = 正在匯入此目錄。<br /><br /> 2 = 沒有正在匯入此目錄。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)   
 [DROP FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md)  
  
  
