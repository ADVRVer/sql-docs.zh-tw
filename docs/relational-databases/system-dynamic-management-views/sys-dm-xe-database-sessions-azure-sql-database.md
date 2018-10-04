---
title: sys.dm_xe_database_sessions，以查看 (Azure SQL Database) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: 33ea5179-16bb-4abd-96cc-9bc696e80987
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 70d7e412dced9f2f1cbf81f1edad5545e59eb857
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765516"
---
# <a name="sysdmxedatabasesessions-azure-sql-database"></a>sys.dm_xe_database_sessions (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  傳回有關工作階段事件的資訊。 事件是不連續的執行點。 述詞可以套用至事件，以便在事件不包含必要資訊時阻止事件引發。  
  
||  
|-|  
|**適用於**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 及更新的版本。|  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|事件工作階段的記憶體位址。 不可為 Null。|  
|event_name|**nvarchar(60)**|動作繫結之事件的名稱。 不可為 Null。|  
|event_package_guid|**uniqueidentifier**|包含此事件之封裝的 GUID。 不可為 Null。|  
|event_predicate|**nvarchar(2048)**|套用至事件之述詞樹狀結構的 XML 表示。 可為 Null。|  
  
## <a name="permissions"></a>Permissions  
 需要 VIEW DATABASE STATE 權限。  
  
### <a name="relationship-cardinalities"></a>關聯性基數  
截至 2015年-07-13 'sys.dm_xe_objects' 是 '（_d）' 在其名稱中的不包含這些 XEvents Dmv。 不是錯字或下列資料表的右邊資料行中的錯誤。 Microsoft SQL Server 和 Azure SQL Database 中的相同名稱。 GeneMi。  
  
|來源|若要|關聯性|  
|--------|------|----------------|  
|sys.dm_xe_database_session_events.event_session_address|sys.dm_xe_database_sessions.address|多對一|  
|sys.dm_xe_database_session_events.event_package_guid、 sys.dm_xe_database_session_events.event_name|sys.dm_xe_objects.name, sys.dm_xe_objects.package_guid|多對一|  
  
## <a name="see-also"></a>另請參閱  
[Azure SQL Database 中擴充的事件](http://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/)  
[擴充事件](../../relational-databases/extended-events/extended-events.md)  
  
 
