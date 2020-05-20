---
title: sys.databases database_mirroring_endpoints （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dc4f44e1b1d935f1abbd49532149edf078f7d1f7
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82823501"
---
# <a name="sysdatabase_mirroring_endpoints-transact-sql"></a>sys.database_mirroring_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  包含一個資料列，代表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的資料庫鏡像端點。  
  
> [!NOTE]  
>  資料庫鏡像端點支援資料庫鏡像夥伴和見證之間的會話，以及 Always On 可用性群組的主要複本與其次要複本之間的會話。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**\<繼承的資料行>**|-|從**sys.databases**繼承資料行（如需詳細資訊，請參閱[sys.databases &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)）。|  
|**role**|**tinyint**|鏡像角色，它有下列幾種：<br /><br /> **0** = 無<br /><br /> **1** = 合作夥伴<br /><br /> **2** = 見證<br /><br /> **3** = 全部<br /><br /> 注意：此值僅與資料庫鏡像相關。|  
|**role_desc**|**nvarchar(60)**|鏡像角色的描述，它有下列幾種：<br /><br /> **NONE**<br /><br /> **搭檔**<br /><br /> **證明**<br /><br /> **ALL**<br /><br /> 注意：此值僅與資料庫鏡像相關。|  
|**is_encryption_enabled**|**bit**|**1**表示加密已啟用。<br /><br /> **0**表示已停用加密。|  
|**connection_auth**|**tinyint**|與這個端點連接所需的連接驗證類型，它有下列幾種：<br /><br /> **1** -NTLM<br /><br /> **2** -KERBEROS<br /><br /> **3** -NEGOTIATE<br /><br /> **4** -憑證<br /><br /> **5** -NTLM、憑證<br /><br /> **6** -KERBEROS、憑證<br /><br /> **7** -NEGOTIATE，憑證<br /><br /> **8** -憑證、NTLM<br /><br /> **9** -憑證、KERBEROS<br /><br /> **10** -CERTIFICATE、NEGOTIATE|  
|**connection_auth_desc**|**Nvarchar (60)**|與這個端點連接所需之驗證類型的描述，它有下列幾種：<br /><br /> NTLM<br /><br /> KERBEROS<br /><br /> NEGOTIATE<br /><br /> CERTIFICATE<br /><br /> NTLM、CERTIFICATE<br /><br /> KERBEROS、CERTIFICATE<br /><br /> NEGOTIATE、CERTIFICATE<br /><br /> CERTIFICATE、NTLM<br /><br /> CERTIFICATE、KERBEROS<br /><br /> CERTIFICATE、NEGOTIATE|  
|**certificate_id**|**int**|驗證所用的憑證識別碼 (如果有的話)。<br /><br /> 0 = 正在使用 Windows 驗證。|  
|**encryption_algorithm**|**tinyint**|加密演算法，它有下列幾種：<br /><br /> **0** -無<br /><br /> **1** -RC4<br /><br /> **2** -AES<br /><br /> **3** -NONE、RC4<br /><br /> **4** -NONE、AES<br /><br /> **5** -RC4、AES<br /><br /> **6** -AES、RC4<br /><br /> **7** -NONE、RC4、AES<br /><br /> **8** -NONE、AES、RC4|  
|**encryption_algorithm_desc**|**nvarchar(60)**|加密演算法的描述，它有下列幾種：<br /><br /> 無<br /><br /> RC4<br /><br /> AES<br /><br /> NONE、RC4<br /><br /> NONE、AES<br /><br /> RC4、AES<br /><br /> AES、RC4<br /><br /> NONE、RC4、AES<br /><br /> NONE、AES、RC4|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]  
>  只有 RC4 演算法支援回溯相容性。 只有在資料庫相容性層級為 90 或 100 時，才能使用 RC4 或 RC4_128 加密新資料  (不建議使用)。請改用較新的演算法，例如其中一個 AES 演算法。 在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 和更新版本中使用 RC4 或 RC4_128 加密的資料，可以在任何相容性層級進行解密。  
  
## <a name="permissions"></a>權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在新增或修改可用性複本時指定端點 URL &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)   
 [availability_replicas &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)   
 [database_mirroring &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md)   
 [database_mirroring_witnesses &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [資料庫鏡像端點 &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [查詢 SQL Server 系統目錄 FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
