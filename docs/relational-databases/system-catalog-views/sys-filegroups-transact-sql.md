---
title: sys.databases （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.filegroups_TSQL
- filegroups
- sys.filegroups
- filegroups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filegroups catalog view
ms.assetid: 9e851f72-1f8e-4515-a25d-152ebc12ed56
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4e143c5f995c05b7bf23f62f36ea5681621cccab
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828144"
---
# <a name="sysfilegroups-transact-sql"></a>sys.filegroups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  針對身為檔案群組的每個資料空間，各包含一個資料列。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**\<繼承的資料行>**|--|如需此視圖所繼承之資料行的清單，請參閱[data_spaces &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)。|  
|**filegroup_guid**|**uniqueidentifier**|檔案群組的 GUID。<br /><br /> NULL = PRIMARY 檔案群組|  
|**log_filegroup_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，這個值是 NULL。|  
|**is_read_only**|**bit**|1 = 檔案群組是唯讀的。<br /><br /> 0 = 檔案群組是可讀寫的。|  
|**is_autogrow_all_files**|**bit**|**適用**于： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] （ [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至[目前版本](https://go.microsoft.com/fwlink/p/?LinkId=299658)）。<br /><br /> 1 = 當檔案群組中的檔案符合自動成長閾值時，檔案群組中的所有檔案都會成長。<br /><br /> 0 = 當檔案群組中的檔案符合自動成長閾值時，只有該檔案會變大。 此為預設值。|  
  
## <a name="permissions"></a>權限  
 需要 **public** 角色的成員資格。  如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的目錄檢視](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [&#40;Transact-sql&#41;的資料空間](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)  
  
  
