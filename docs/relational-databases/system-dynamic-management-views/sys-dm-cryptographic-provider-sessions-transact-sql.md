---
description: sys.dm_cryptographic_provider_sessions (Transact-SQL)
title: sys. dm_cryptographic_provider_sessions (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_cryptographic_provider_sessions
- dm_cryptographic_provider_sessions_TSQL
- sys.dm_cryptographic_provider_sessions_TSQL
- dm_cryptographic_provider_sessions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_sessions dynamic management function
ms.assetid: 9a4de02b-1a07-4850-979a-0861fddb7f9d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 37a8854da08439c4dc3984bcdfc61a8695467c2b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88455010"
---
# <a name="sysdm_cryptographic_provider_sessions-transact-sql"></a>sys.dm_cryptographic_provider_sessions (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  傳回有關針對密碼編譯提供者所開啟之工作階段的資訊。  
 
## <a name="syntax"></a>語法  
  
```  
  
sys.dm_cryptographic_provider_sessions(session_identifier)  
```  
  
## <a name="arguments"></a>引數  
 *session_identifier*  
 表示要傳回之工作階段的整數。  
  
 0 = 僅限目前的連接  
  
 1 = 所有密碼編譯連接  
  
## <a name="table-returned"></a>傳回的資料表  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**provider_id**|**int**|密碼編譯提供者的識別碼。|  
|**session_handle**|**varbytes (8) **|密碼編譯工作階段控制代碼。|  
|**身分識別**|**nvarchar(128)**|利用密碼編譯提供者驗證所使用的識別。|  
|**spid**|**short**|連接的工作階段識別碼 SPID。 如需詳細資訊，請參閱 [@@SPID &#40;Transact-SQL&#41;](../../t-sql/functions/spid-transact-sql.md)。|  
  
## <a name="remarks"></a>備註  
 目前連接的公用可以看到 **sys. dm_cryptographic_provider_sessions** view。 若要查看所有密碼編譯連接，您必須具有 **CONTROL** server 許可權。  
  
## <a name="see-also"></a>另請參閱  
 [安全性目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [可延伸金鑰管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [加密階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
