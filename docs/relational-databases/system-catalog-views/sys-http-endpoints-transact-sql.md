---
title: sys.http_endpoints (TRANSACT-SQL) |Microsoft 文件
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
- sys.http_endpoints
- http_endpoints
- sys.http_endpoints_TSQL
- http_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.http_endpoints catalog view
ms.assetid: 16f59695-ecd9-457e-8874-055af63f8ea7
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 6b6c0182715a823a481224295839cc7b61fda210
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="syshttpendpoints-transact-sql"></a>sys.http_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對使用 HTTP 通訊協定的伺服器中所建立的每個端點，各包含一個資料列。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**< 繼承的資料行 >**||繼承資料行從[sys.endpoints &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)。|  
|**站台**|**nvarchar(128)**|依照 SITE = 選項所指定的網站主機電腦名稱。|  
|**url_path**|**nvarchar(4000)**|依照 PATH= 選項所指定，這個 HTTP 端點的 URL 只有路徑的部份。|  
|**is_clear_port_enabled**|**bit**|1 = 利用 PORT = CLEAR 選項來啟用清除通訊埠|  
|**clear_port**|**int**|CLEAR PORT = 選項所指定的通訊埠編號。<br /><br /> NULL = 未指定。|  
|**is_ssl_port_enabled**|**bit**|1 = 利用 PORT = SSL 選項來啟用 SSL 埠。|  
|**ssl_port**|**int**|SSL PORT = 選項所指定的通訊埠編號值。<br /><br /> NULL = 未指定。|  
|**is_anonymous_enabled**|**bit**|1 = 利用 AUTHENTICATION = ANONYMOUS 選項來啟用匿名存取。|  
|**is_basic_auth_enabled**|**bit**|1 = 利用 AUTHENTICATION = BASIC 選項來啟用基本驗證。|  
|**is_digest_auth_enabled**|**bit**|1 = 利用 AUTHENTICATION = DIGEST 選項來啟用摘要驗證。|  
|**is_kerberos_auth_enabled**|**bit**|1 = 利用 AUTHENTICATION = KERBEROS 選項來啟用整合式驗證。|  
|**is_ntlm_auth_enabled**|**bit**|1 = 利用 AUTHENTICATION = NTLM 選項來啟用整合式驗證。|  
|**is_integrated_auth_enabled**|**bit**|1 = 利用 AUTHENTICATION = INTEGRATED 選項來啟用整合式驗證。|  
|**authorization_realm**|**nvarchar(128)**|在 HTTP DIGEST 驗證挑戰中傳回用戶端的提示。 這是 AUTH REALM 選項的值。<br /><br /> 如果並未指定，或未啟用 DIGEST 驗證，便是 NULL。|  
|**default_logon_domain**|**nvarchar(128)**|如果您啟用 BASIC 驗證，便是預設登入網域。 這是 DEFAULT LOGON DOMAIN 選項的值。<br /><br /> 如果並未指定，或未啟用 BASIC 驗證，便是 NULL。|  
|**is_compression_enabled**|**bit**|1 = 設定 COMPRESSION = ENABLED 選項。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [端點目錄檢視&#40;Transact SQL&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  
