---
title: sys. dm_xe_database_session_event_actions
titleSuffix: Azure SQL Database
ms.custom: seo-lt-2019
ms.date: 06/10/2016
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 48519fd9-c7c2-434b-848d-ccbf41133fdd
author: MightyPen
ms.author: genemi
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 322a54a4f3bbd5f4880df6f52a085f5d7141d335
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2019
ms.locfileid: "73844454"
---
# <a name="sysdm_xe_database_session_event_actions-azure-sql-database"></a>sys.dm_xe_database_session_event_actions (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  傳回有關事件工作階段動作的資訊。 事件引發時，會執行動作。 這個管理檢視會彙總有關動作已執行之次數及動作之執行時間總計的統計資料。  
  
||  
|-|  
|**適用于**： [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 和任何未來版本。|  
  
|資料行名稱|資料類型|說明|  
|-----------------|---------------|-----------------|  
|event_session_address|**Varbinary （8）**|事件工作階段的記憶體位址。 不可為 Null。|  
|action_name|**nvarchar(60)**|動作的名稱。 不可為 Null。|  
|action_package_guid|**uniqueidentifier**|包含此動作之封裝的 GUID。 不可為 Null。|  
|event_name|**nvarchar(60)**|此動作繫結之事件的名稱。 不可為 Null。|  
|event_package_guid|**uniqueidentifier**|包含此事件之封裝的 GUID。 不可為 Null。|  
  
## <a name="permissions"></a>Permissions  
 需要 VIEW DATABASE STATE 權限。  
  
### <a name="relationship-cardinalities"></a>關聯性基數  
  
|來源|若要|[關聯性]|  
|----------|--------|------------------|  
|dm_xe_database_session_event_actions. event_session_address|dm_xe_database_sessions 位址|多對一|  
|dm_xe_database_session_event_actions. action_name<br /><br /> sys.dm_xe_session_event_actions.action_package_guid|sys.dm_xe_objects.name<br /><br /> dm_xe_database_session_events. event_package_guid|多對一|  
|dm_xe_database_session_event_actions. event_name<br /><br /> dm_xe_database_session_event_actions. event_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_objects.package_guid|多對一|  
  
## <a name="see-also"></a>另請參閱  
 [擴充事件](../../relational-databases/extended-events/extended-events.md)  
  
  
