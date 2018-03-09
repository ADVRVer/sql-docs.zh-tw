---
title: "建立追蹤 (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-trace
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], example
- traces [SQL Server], creating
ms.assetid: 79dd4254-e3c6-467a-bb6f-f99e51757e99
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d56ed4af251bb739c6717afa6373d4eac1ed9105
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="create-a-trace-transact-sql"></a>建立追蹤 (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
此主題描述如何使用預存程序來建立追蹤。  
  
### <a name="to-create-a-trace"></a>若要建立追蹤  
  
1.  執行 **sp_trace_create** 並加上必要的參數，以建立新的追蹤。 新的追蹤會處於停止狀態 (*status* 為 **0**)。  
  
2.  執行 **sp_trace_setevent** 並加上必要的參數，以選取要追蹤的事件和資料行。  
  
3.  (選擇性) 執行 **sp_trace_setfilter** 以設定任何篩選或篩選組合。  
  
     **sp_trace_setevent** 和 **sp_trace_setfilter** 只能在已停止的現有追蹤上執行。  
  
    > [!IMPORTANT]  
    >  和一般的預存程序不同，所有 SQL Server Profiler 預存程序 (**sp_trace_*xx***) 的參數均嚴格分類，且不支援自動資料類型的轉換。 如果沒有依照引數描述所指定，以正確的輸入參數資料類型來呼叫這些參數，預存程序會傳回錯誤。  
  
## <a name="example"></a>範例  
 下列程式碼將示範如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]來建立追蹤。 這個程式碼含有三個區段：建立追蹤、擴展追蹤檔案以及停止追蹤。 您可以透過加入想要追蹤的事件，自訂追蹤。 如需事件和資料行的清單，請參閱 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)來建立追蹤。  
  
 下列程式碼會建立追蹤、將事件加入至追蹤，然後啟動追蹤：  
  
```  
DECLARE @RC int, @TraceID int, @on BIT  
EXEC @rc = sp_trace_create @TraceID output, 0, N'C:\SampleTrace'  
  
-- Select the return code to see if the trace creation was successful.  
SELECT RC = @RC, TraceID = @TraceID  
  
-- Set the events and data columns you need to capture.  
SELECT @on = 1  
  
-- 10 is RPC:Completed event. 1 is TextData column.   
EXEC sp_trace_setevent @TraceID, 10, 1, @on   
-- 13 is SQL:BatchStarting, 11 is LoginName  
EXEC sp_trace_setevent @TraceID, 13, 11, @on   
-- 13 is SQL:BatchStarting, 14 is StartTime  
EXEC sp_trace_setevent @TraceID, 13, 14, @on   
-- 12 is SQL:BatchCompleted, 15 is EndTime  
EXEC sp_trace_setevent @TraceID, 12, 15, @on   
-- 13 is SQL:BatchStarting, 1 is TextData  
EXEC sp_trace_setevent @TraceID, 13, 1, @on   
  
-- Set any filter. Not provided in this example  
--EXEC sp_trace_setfilter 1, 10, 0, 6, N'%Profiler%'  
  
-- Start Trace (status 1 = start)  
EXEC @RC = sp_trace_setstatus @TraceID, 1  
GO  
  
```  
  
## <a name="example"></a>範例  
 此時您已經建立並啟動追蹤，請執行下列程式碼，使用活動來擴展追蹤。  
  
```  
SELECT * FROM master.sys.databases  
GO  
SELECT * FROM ::fn_trace_getinfo(default)  
GO  
  
```  
  
## <a name="example"></a>範例  
 您可以隨時停止並重新啟動追蹤。 在這個範例中，請執行下列程式碼來停止追蹤、關閉追蹤，然後刪除追蹤定義。  
  
```  
DECLARE @TraceID int  
-- Populate a variable with the trace_id of the current trace  
SELECT  @TraceID = TraceID FROM ::fn_trace_getinfo(default) WHERE VALUE = N'C:\SampleTrace.trc'  
  
-- First stop the trace.   
EXEC sp_trace_setstatus @TraceID, 0  
  
-- Close and then delete its definition from SQL Server.   
EXEC sp_trace_setstatus @TraceID, 2  
  
```  
  
## <a name="example"></a>範例  
 若要檢查追蹤檔案，請使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]來開啟 SampleTrace.trc 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Profiler 預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)   
 [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)  
  
  
