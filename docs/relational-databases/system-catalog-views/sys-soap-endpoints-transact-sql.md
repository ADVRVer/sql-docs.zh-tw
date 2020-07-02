---
title: sys.databases soap_endpoints （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- soap_endpoints_TSQL
- sys.soap_endpoints
- soap_endpoints
- sys.soap_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.soap_endpoints catalog view
ms.assetid: f50dcbfc-02ed-4a19-9c07-c78a5a1b3224
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6cb269ec8ce866e02dcb4ea06a7fe66f0c49e5a5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750689"
---
# <a name="syssoap_endpoints-transact-sql"></a>sys.soap_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 針對伺服器中存放 SOAP 類型裝載的每個端點，各包含一個資料列。 針對此視圖中的每個資料列，在具有 HTTP 設定中繼資料的**sys.databases HTTP_endpoints**目錄檢視中，有一個對應的資料列具有相同的**endpoint_id** 。  
  
 
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**< 繼承的資料行>**||如需此視圖所繼承之資料行的清單，請參閱[&#40;transact-sql&#41;的 sys.databases ](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)。|  
|**is_sql_language_enabled**|**bit**|指定 1 = BATCHES = ENABLED 選項，表示該端點可以有特定的 SQL 批次。|  
|**wsdl_generator_procedure**|**Nvarchar （776）**|實作這個方法之預存程序的三部份名稱。<br /><br /> 方法的名稱必須遵循三部分的語法。 一部分、二部分及四部分的名稱皆不可使用。|  
|**default_database**|**sysname**|DATABASE = 選項中所給定的預設資料庫名稱。<br /><br /> 指定 NULL = DEFAULT。|  
|**default_namespace**|**Nvarchar （384）**|NAMESPACE = 選項中所指定的預設命名空間， `https://tempuri.org` 如果改為指定 default，則為。|  
|**default_result_schema**|**tinyint**|SCHEMA = 選項的預設值。<br /><br /> 0 = NONE<br /><br /> 1 = STANDARD|  
|**default_result_schema_desc**|**nvarchar(60)**|SCHEMA = 選項的預設值描述。<br /><br /> NONE<br /><br /> STANDARD|  
|**is_xml_charset_enforced**|**bit**|已指定 0 = CHARACTER_SET = SQL 選項。<br /><br /> 已指定 1 = CHARACTER_SET = XML 選項。|  
|**is_session_enabled**|**bit**|已指定 0 = SESSION = DISABLE 選項。<br /><br /> 已指定 1 = SESSION = ENABLED 選項。|  
|**session_timeout**|**int**|在 SESSION_TIMEOUT = 選項中指定的值。|  
|**login_type**|**nvarchar(60)**|這個端點所接受的驗證種類。<br /><br /> WINDOWS<br /><br /> MIXED|  
|**header_limit**|**int**|SOAP 標頭所能接受的最大值。|  
  
## <a name="permissions"></a>權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [端點目錄檢視 &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
