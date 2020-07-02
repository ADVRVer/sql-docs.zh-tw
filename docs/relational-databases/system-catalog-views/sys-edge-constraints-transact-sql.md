---
title: sys.databases edge_constraints （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.edge_constraints
- edge_constraints
- SQL Graph
- edge_constraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.edge_constraints catalog view
ms.assetid: 0f782d2f-7126-46ab-85b7-bcba44862231
author: shkale-msft
ms.author: shkale
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9e3e7068e18e5a0315936593fca071132d49e833
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85648908"
---
# <a name="sysedge_constraints-transact-sql"></a>sys.databases edge_constraints （Transact-sql）
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx.md](../../includes/applies-to-version/sqlserver2019.md)]

針對每個做為邊緣條件約束的物件，各包含一個資料列。 
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**\<Columns inherited from sys.objects>**||如需此視圖所繼承之資料行的清單，請參閱[sys.databases &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)。|  
|**is_disabled**|**bit**|1 = 邊緣條件約束是 disbled。<br /><br /> 0 = 已啟用邊緣條件約束。|  
|**is_not_trusted**|**bit**|1 = 邊緣條件約束尚未被系統驗證。<br /><br /> 0 = Edge 條件約束已由系統驗證。|  
|**delete_referential_action**|**tinyint**|在此邊緣條件約束上定義的參考動作。<br /><br />0 = 沒有動作。|  
|**delete_referential_action_desc**|**nvarchar(60)**|在此邊緣條件約束上定義之參考動作的描述。<br /><br />NO_ACTION|  
|**is_system_named**|**bit**|1 = 邊緣條件約束名稱由系統產生。<br /><br />0 = 邊緣條件約束名稱是由使用者提供。|  
  
## <a name="permissions"></a>權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的物件目錄檢視](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [&#40;Transact-sql&#41;的目錄檢視](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [查詢 SQL Server 系統目錄 FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
