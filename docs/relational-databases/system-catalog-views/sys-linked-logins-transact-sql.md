---
title: sys.databases linked_logins （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.linked_logins
- sys.linked_logins_TSQL
- linked_logins_TSQL
- linked_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.linked_logins catalog view
ms.assetid: af57bf0c-a265-410f-9bab-63b78569b4a6
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 3182516451f88d25bbd2d6e1e08884f638dea02c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85783977"
---
# <a name="syslinked_logins-transact-sql"></a>sys.linked_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  針對每個連結伺服器登入對應，各傳回一個資料列，讓 RPC 和分散式查詢從本機伺服器對應至對應的連結伺服器。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|**Sys.databases**中的伺服器識別碼。|  
|**local_principal_id**|**int**|對應所套用至的伺服器主體。<br /><br /> 0 = wildcard 或 public。|  
|**uses_self_credential**|**bit**|如果是 1，則對應會指出工作階段應該使用其本身的認證；否則就是 0，表示工作階段應該使用提供的名稱和密碼。|  
|**remote_name**|**sysname**|在連接時所要使用的遠端使用者名稱。 也會儲存密碼，但不會顯示在目錄檢視介面上。|  
|**modify_date**|**datetime**|上次變更連結登入的日期。|  
  
## <a name="permissions"></a>權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的目錄檢視](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [連結伺服器目錄檢視 &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)  
  
  
