---
title: sys.databases HTTP_endpoints （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b64effb7ef97231ef4620c6dd2d19d5783aea943
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828463"
---
# <a name="syshttp_endpoints-transact-sql"></a>sys.http_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對使用 HTTP 通訊協定的伺服器中所建立的每個端點，各包含一個資料列。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**< 繼承的資料行>**||從 sys.databases 繼承[&#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)的資料行。|  
|**點**|**nvarchar(128)**|依照 SITE = 選項所指定的網站主機電腦名稱。|  
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
  
## <a name="permissions"></a>權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的目錄檢視](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [端點目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  
