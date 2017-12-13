---
title: "在 DirectQuery 模式中測試模型 |Microsoft 文件"
ms.custom: 
ms.date: 07/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11260792-ff8b-4d0e-b845-ca210dd3fced
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 430bfd1f58ea15ab04fb57f7f806191a57bc2d4e
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2017
---
# <a name="test-a-model-in-directquery-mode"></a>在 DirectQuery 模式中測試模型
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]檢閱測試的表格式模型在 DirectQuery 模式中，程式開發，從設計開始著手的每個階段的選項。  
  
## <a name="test-in-excel"></a>在 Excel 中進行測試 
  
 在 SSDT 中設計模型時，您可以使用 [在 Excel 中進行分析] 功能針對記憶體內部的範例資料集或關聯式資料庫，測試您的模型化決策。  當您按一下 [在 Excel 中進行分析] 時，會開啟對話方塊讓您指定選項。
 
 ![在 Excel DirectQuery 選項中進行分析](../../analysis-services/tabular-models/media/analyze-in-excel-directquery-options.png)
 
 如果開啟了模型的 DirectQuery 模式，即可指定 DirectQuery 連接模式，在此有兩個選項︰
 - **範例資料檢視** ：使用此選項，任何 Excel 查詢都會導向至含有記憶體內部範例資料集的範例資料分割。 當您想要確定您在量值、導出資料行或資料列層級安全性的任何 DAX 公式會正確執行時，此選項會很有用。
 
 - **完整資料檢視** ：使用此選項，任何 Excel 查詢都會先傳送至 Analysis Services，再到關聯式資料庫。 其實，此選項能完全發揮 DirecQuery 模式的作用。
 
 ### <a name="other-clients"></a>其他用戶端
 當您使用 [在 Excel 中進行分析] 時，會建立 .odc 連接檔案。 您可以使用這個檔案的連接字串資訊，從其他用戶端應用程式連接到您的模型。 加入額外的參數 DataView=Sample，則指定用戶端應該連接到範例資料分割。  
  
## <a name="monitor-query-execution-on-backend-systems-using-xevents-or-sql-profiler"></a>使用 xEvents 或 SQL Profiler 監視後端系統上的查詢執行 
 啟動工作階段追蹤，並連接到 SQL Server 關聯式資料庫，以監視來自表格式模型的連接︰  
  
-   [使用 SQL Server 擴充事件監視 Analysis Services](../../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)  
  
-   [使用 SQL Server Profiler 監視 Analysis Services](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)  
  
 如果使用的是 Oracle 或 Teradata，請使用這些系統的追蹤監視工具。  
  
  
