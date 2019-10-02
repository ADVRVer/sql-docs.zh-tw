---
title: 使用擴充事件監視 Python 和 R 腳本
description: 瞭解如何使用擴充事件來監視和疑難排解與 SQL Server Machine Learning 服務、SQL Server Launchpad 和 Python 或 R 作業外部腳本相關的操作。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6faef1bd78b1c1aa42714da75679dc989f0b9da9
ms.sourcegitcommit: fd3e81c55745da5497858abccf8e1f26e3a7ea7d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71714382"
---
# <a name="monitor-python-and-r-scripts-with-extended-events-in-sql-server-machine-learning-services"></a>使用 SQL Server Machine Learning Services 中的擴充事件來監視 Python 和 R 腳本
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

瞭解如何使用擴充事件來監視和疑難排解與 SQL Server Machine Learning 服務、SQL Server Launchpad 和 Python 或 R 作業外部腳本相關的操作。

## <a name="extended-events-for-sql-server-machine-learning-services"></a>SQL Server Machine Learning 服務的擴充事件

若要查看與 SQL Server Machine Learning 服務相關的事件清單，請從 Azure Data Studio 或 SQL Server Management Studio 執行下列查詢。

```sql
SELECT o.name AS event_name, o.description
FROM sys.dm_xe_objects o
JOIN sys.dm_xe_packages p
ON o.package_guid = p.guid
WHERE o.object_type = 'event'
AND p.name = 'SQLSatellite';
```

如需如何使用擴充事件的詳細資訊，請參閱[擴充事件工具](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools)。

## <a name="additional-events-specific-to-machine-learning-services"></a>Machine Learning 服務特定的其他事件

其他擴充事件適用于與 SQL Server Machine Learning 服務相關的元件，例如 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] 和 BXLServer，以及啟動 Python 或 R 執行時間的附屬進程。 這些額外的擴充事件會從外部進程引發;因此，您必須使用外部公用程式來加以捕捉。

如需如何執行此作業的詳細資訊, 請參閱[從外部進程收集事件](#bkmk_externalevents)一節。

<a name="bkmk_xeventtable"></a> 

## <a name="table-of-extended-events"></a>擴充事件的資料表

|Event - 事件|描述|注意|  
|-----------|-----------------|---------|  
|connection_accept|接受新連線時會發生。 此事件是用來記錄所有的連線嘗試。||  
|failed_launching|啟動失敗。|表示發生錯誤。|  
|satellite_abort_connection|中止連接記錄||  
|satellite_abort_received|透過附屬連線收到中止訊息時引發。||  
|satellite_abort_sent|透過附屬連線傳送中止訊息時引發。||  
|satellite_authentication_completion|完成透過 TCP 或 Namedpipe 連線的驗證時引發。||  
|satellite_authorization_completion|完成透過 TCP 或 Namedpipe 連線的授權時引發。||  
|satellite_cleanup|清除附屬呼叫時引發。|只會從外部處理序引發。 檢視從外部處理序收集事件的指示。|  
|satellite_data_chunk_sent|附屬連線完成傳送單一資料區塊時引發。|事件會報告已傳送的資料列數目、資料行數目、所使用的 SNI 封包數目，以及送出區塊時所經過的時間（以毫秒為單位）。 此資訊可協助您了解傳送不同類型的資料花費多少時間，以及使用多少封包。|  
|satellite_data_receive_completion|透過附屬連線收到查詢要求的所有資料時引發。|只會從外部處理序引發。 檢視從外部處理序收集事件的指示。|  
|satellite_data_send_completion|透過附屬連線傳送工作階段要求的所有資料時引發。||  
|satellite_data_send_start|在資料傳輸開始時引發。| 資料傳輸會在傳送第一個資料區塊之前啟動。|  
|satellite_error|用來追蹤 SQL 附屬錯誤||  
|satellite_invalid_sized_message|訊息的大小無效||  
|satellite_message_coalesced|用來追蹤網路層的訊息聯合||  
|satellite_message_ring_buffer_record|訊息信號緩衝區記錄||  
|satellite_message_summary|訊息傳遞的相關摘要資訊||  
|satellite_message_version_mismatch|訊息的版本欄位不相符||  
|satellite_messaging|用來追蹤訊息事件 (繫結、解除繫結等)||  
|satellite_partial_message|用來追蹤網路層的部分訊息||  
|satellite_schema_received|在 SQL 收到並讀取結構描述訊息時引發。||  
|satellite_schema_sent|透過附屬處理序傳送結構描述訊息時引發。|只會從外部處理序引發。 檢視從外部處理序收集事件的指示。|  
|satellite_service_start_posted|在服務啟動訊息張貼到啟動控制板時引發。|這會通知啟動控制板啟動外部處理序，且其中包含新工作階段的識別碼。|  
|satellite_unexpected_message_received|收到非預期的訊息時引發。|表示發生錯誤。|  
|stack_trace|在要求處理序的記憶體傾印時發生。|表示發生錯誤。|  
|trace_event|用來進行追蹤|這些事件可以包含 SQL Server、啟動控制板和外部處理序追蹤訊息。 包含從 R 輸出至 stdout 和 stderr。|  
|launchpad_launch_start|啟動板開始啟動附屬處理序時引發。|只能從啟動控制板引發。 檢視從 launchpad.exe 收集事件的指示。|  
|launchpad_resume_sent|啟動控制板啟動附屬處理序並將繼續訊息傳送至 SQL Server 時引發。|只能從啟動控制板引發。 檢視從 launchpad.exe 收集事件的指示。|  
|satellite_data_chunk_sent|附屬連線完成傳送單一資料區塊時引發。|包含有關資料行數目、資料列數目、封包數目及傳送區塊所經過之時間的資訊。|  
|satellite_sessionId_mismatch|訊息的會話識別碼不是預期的||  

<a name="bkmk_externalevents"></a>

### <a name="collecting-events-from-external-processes"></a>從外部進程收集事件

SQL Server Machine Learning 服務會啟動一些在 SQL Server 進程外執行的服務。 若要捕捉與這些外部進程相關的事件, 您必須建立事件追蹤設定檔案, 並將該檔案放在與該處理常式可執行檔相同的目錄中。  
  
+ **[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]**   
  
    若要擷取與 Launchpad 相關的事件，請將 *.config* 檔案放在 SQL Server 執行個體的 Binn 目錄中。 在預設安裝中, 這會是:

    `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\MSSQL\Binn`.  
  
+ **BXLServer**是使用外部指令碼語言 (例如 R 或 Python) 支援 SQL 擴充性的附屬進程。 會針對每個外部語言實例啟動個別的 BxlServer 實例。
  
    若要捕捉與 BXLServer 相關的事件, 請將 *.config*檔案放在 R 或 Python 安裝目錄中。 在預設安裝中, 這會是:
     
    **R:** `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64`.  

    **Python:** `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\PYTHON_SERVICES\library\RevoScaleR\rxLibs\x64`.

設定檔的名稱必須與可執行檔相同，使用格式為 "[name]. xevents .xml"。 也就是說，檔案必須用以下的格式命名︰

+ `Launchpad.xevents.xml`
+ `bxlserver.xevents.xml`

組態檔本身的格式如下：

```xml
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
<event_session name="[session name]" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="you">Xevent for launchpad or bxl server.</description>  
    <event package="SQLSatellite" name="[XEvent Name 1]" />  
    <event package="SQLSatellite" name="[XEvent Name 2]" />  
    <target package="package0" name="event_file">  
      <parameter name="filename" value="[SessionName].xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
```

+ 若要設定追蹤, 請編輯*會話名稱*預留位置、檔案名的預留位置 (`[SessionName].xel`), 以及您想要捕獲的事件名稱`[XEvent Name 1]`, `[XEvent Name 1]`例如,)。  
+ 可能會出現任意數目的事件封裝標記, 只要 name 屬性正確就會收集。

### <a name="example-capturing-launchpad-events"></a>範例：正在捕獲啟動控制板事件

下列範例顯示啟動控制板服務的事件追蹤定義:

```xml
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
<event_session name="sqlsatelliteut" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="hay">Xevent for sql tdd runner.</description>  
    <event package="SQLSatellite" name="launchpad_launch_start" />  
    <event package="SQLSatellite" name="launchpad_resume_sent" />  
    <target package="package0" name="event_file">  
      <parameter name="filename" value="launchpad_session.xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
```

+ 將 *.config* 檔案放在 SQL Server 執行個體的 Binn 目錄中。
+ 這個檔案必須命名為`Launchpad.xevents.xml`。

### <a name="example-capturing-bxlserver-events"></a>範例：捕捉 BXLServer 事件  

以下範例顯示 BXLServer 可執行檔的事件追蹤。
  
```xml
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
 <event_session name="sqlsatelliteut" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="hay">Xevent for sql tdd runner.</description>  
    <event package="SQLSatellite" name="satellite_abort_received" />  
    <event package="SQLSatellite" name="satellite_authentication_completion" />  
    <event package="SQLSatellite" name="satellite_cleanup" />  
    <event package="SQLSatellite" name="satellite_data_receive_completion" />  
    <event package="SQLSatellite" name="satellite_data_send_completion" />  
    <event package="SQLSatellite" name="satellite_data_send_start" />  
    <event package="SQLSatellite" name="satellite_schema_sent" />   
    <event package="SQLSatellite" name="satellite_unexpected_message_received" />    
    <event package="SQLSatellite" name="satellite_data_chunk_sent" />   
    <target package="package0" name="event_file">  
      <parameter name="filename" value="satellite_session.xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
```

+ 將 *.config* 檔案放在 BXLServer 可執行檔所在的相同目錄中。
+ 這個檔案必須命名為`bxlserver.xevents.xml`。

## <a name="next-steps"></a>後續步驟

- [使用 SQL Server Management Studio 中的自訂報表監視 Python 和 R 腳本執行](../../advanced-analytics/administration/monitor-sql-server-machine-learning-services-using-custom-reports-management-studio.md)
- [使用動態管理檢視（Dmv）監視 SQL Server Machine Learning 服務](../../advanced-analytics/administration/monitor-sql-server-machine-learning-services-using-dynamic-management-views.md)
