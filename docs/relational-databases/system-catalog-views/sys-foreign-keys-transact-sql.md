---
title: sys.databases foreign_keys （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- foreign_keys
- sys.foreign_keys
- sys.foreign_keys_TSQL
- foreign_keys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.foreign_keys catalog view
ms.assetid: e960df1a-13fc-43ee-ba91-34c1b719ac2c
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b78466b0c2c20bc3b59fb372870bbad87aef0e74
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68133893"
---
# <a name="sysforeign_keys-transact-sql"></a>sys.foreign_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  針對每個屬於 FOREIGN KEY 條件約束的物件，各包含一個資料列，其為**sys.databases。類型**= F。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**\<繼承自 sys.databases 的資料行>**||如需此視圖所繼承之資料行的清單，請參閱[sys.databases &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)。|  
|**referenced_object_id**|**int**|被參考的物件識別碼。|  
|**key_index_id**|**int**|被參考的物件內之金鑰索引識別碼。|  
|**is_disabled**|**bit**|FOREIGN KEY 條件約束已停用。|  
|**is_not_for_replication**|**bit**|FOREIGN KEY 條件約束是利用 NOT FOR REPLICATION 選項來建立的。|  
|**is_not_trusted**|**bit**|FOREIGN KEY 條件約束尚未經過系統驗證。|  
|**delete_referential_action**|**tinyint**|在進行刪除時，針對這個 FOREIGN KEY 而宣告的參考動作。<br /><br /> 0 = 沒有動作<br /><br /> 1 = 串聯<br /><br /> 2 = 設為 NULL<br /><br /> 3 = 設為預設值|  
|**delete_referential_action_desc**|**Nvarchar （60）**|在進行刪除時，針對這個 FOREIGN KEY 而宣告的參考動作之描述。<br /><br /> NO_ACTION<br /><br /> CASCADE<br /><br /> SET_NULL<br /><br /> SET_DEFAULT|  
|**update_referential_action**|**tinyint**|在進行更新時，針對這個 FOREIGN KEY 而宣告的參考動作。<br /><br /> 0 = 沒有動作<br /><br /> 1 = 串聯<br /><br /> 2 = 設為 NULL<br /><br /> 3 = 設為預設值|  
|**update_referential_action_desc**|**Nvarchar （60）**|在進行更新時，針對這個 FOREIGN KEY 而宣告的參考動作之描述。<br /><br /> NO_ACTION<br /><br /> CASCADE<br /><br /> SET_NULL<br /><br /> SET_DEFAULT|  
|**is_system_named**|**bit**|1 = 名稱是系統所產生。<br /><br /> 0 = 名稱是使用者所提供。|  
  
## <a name="permissions"></a>權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [&#40;Transact-sql&#41;的物件目錄檢視](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [查詢 SQL Server 系統目錄 FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
