---
title: sys.database_mirroring_endpoints (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.database_mirroring_endpoints_TSQL
- database_mirroring_endpoints
- sys.database_mirroring_endpoints
- database_mirroring_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], endpoint
- HADR [SQL Server], endpoint
- database mirroring [SQL Server], catalog views
- sys.database_mirroring_endpoints catalog view
ms.assetid: f2285199-97ad-473c-a52d-270044dd862b
caps.latest.revision: 49
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 614a57100ffa8e66b1f03757355605409ac5848f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="sysdatabasemirroringendpoints-transact-sql"></a>sys.database_mirroring_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  包含一個資料列，代表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的資料庫鏡像端點。  
  
> [!NOTE]  
>  資料庫鏡像端點支援工作階段之間的資料庫鏡像夥伴與見證 Always On 可用性群組之主要複本和一個次要複本之間的工作階段。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**\<繼承資料行 >**|—|繼承資料行從**sys.endpoints** (如需詳細資訊，請參閱[sys.endpoints &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md))。|  
|**角色**|**tinyint**|鏡像角色，它有下列幾種：<br /><br /> **0** = 無<br /><br /> **1** = partner<br /><br /> **2** = 見證<br /><br /> **3** = all<br /><br /> 注意： 這個值是只與資料庫鏡像有關。|  
|**role_desc**|**nvarchar(60)**|鏡像角色的描述，它有下列幾種：<br /><br /> **NONE**<br /><br /> **夥伴**<br /><br /> **WITNESS**<br /><br /> **ALL**<br /><br /> 注意： 這個值是只與資料庫鏡像有關。|  
|**is_encryption_enabled**|**bit**|**1**表示啟用加密。<br /><br /> **0**表示停用加密。|  
|**connection_auth**|**tinyint**|與這個端點連接所需的連接驗證類型，它有下列幾種：<br /><br /> **1** -NTLM<br /><br /> **2** -KERBEROS<br /><br /> **3** -交涉<br /><br /> **4** -憑證<br /><br /> **5** -NTLM、 CERTIFICATE<br /><br /> **6** -KERBEROS、 CERTIFICATE<br /><br /> **7** -NEGOTIATE、 CERTIFICATE<br /><br /> **8** -CERTIFICATE、 NTLM<br /><br /> **9** -CERTIFICATE、 KERBEROS<br /><br /> **10** -CERTIFICATE、 NEGOTIATE|  
|**connection_auth_desc**|**nvarchar (60)**|與這個端點連接所需之驗證類型的描述，它有下列幾種：<br /><br /> NTLM<br /><br /> KERBEROS<br /><br /> NEGOTIATE<br /><br /> CERTIFICATE<br /><br /> NTLM、CERTIFICATE<br /><br /> KERBEROS、CERTIFICATE<br /><br /> NEGOTIATE、CERTIFICATE<br /><br /> CERTIFICATE、NTLM<br /><br /> CERTIFICATE、KERBEROS<br /><br /> CERTIFICATE、NEGOTIATE|  
|**certificate_id**|**int**|驗證所用的憑證識別碼 (如果有的話)。<br /><br /> 0 = 正在使用 Windows 驗證。|  
|**encryption_algorithm**|**tinyint**|加密演算法，它有下列幾種：<br /><br /> **0** – NONE<br /><br /> **1** – RC4<br /><br /> **2** – AES<br /><br /> **3** – NONE、 RC4<br /><br /> **4** – NONE、 AES<br /><br /> **5** – RC4、 AES<br /><br /> **6** – AES、 RC4<br /><br /> **7** – NONE、 RC4、 AES<br /><br /> **8** – NONE、 AES、 RC4|  
|**encryption_algorithm_desc**|**nvarchar(60)**|加密演算法的描述，它有下列幾種：<br /><br /> 無<br /><br /> RC4<br /><br /> AES<br /><br /> NONE、RC4<br /><br /> NONE、AES<br /><br /> RC4、AES<br /><br /> AES、RC4<br /><br /> NONE、RC4、AES<br /><br /> NONE、AES、RC4|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]  
>  只有 RC4 演算法支援回溯相容性。 只有在資料庫相容性層級為 90 或 100 時，才能使用 RC4 或 RC4_128 加密新資料  (不建議使用)。請改用較新的演算法，例如其中一個 AES 演算法。 在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 和更新版本中使用 RC4 或 RC4_128 加密的資料，可以在任何相容性層級進行解密。  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [指定端點 URL 中加入或修改可用性複本時&#40;SQL Server&#41;](../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)   
 [sys.availability_replicas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)   
 [sys.database_mirroring &#40;Transact SQL&#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md)   
 [sys.database_mirroring_witnesses &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [資料庫鏡像端點 & #40;SQL Server & #41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [查詢 SQL Server 系統目錄常見問題集](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
