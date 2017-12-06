---
title: "ReportViewer 控制項 2016 中的資料收集 | Microsoft Docs"
ms.custom: 
ms.date: 09/06/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: application-integration
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
caps.latest.revision: "2"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6249d0a0b8b13c47479130c1f981b6756989c4c7
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2017
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>使用 ReportViewer 控制項整合 Reporting Services - 資料收集
根據預設，ReportViewer 控制項會匿名收集使用方式資訊，以便讓 Microsoft 進一步了解客戶如何使用控制項。 藉由進一步了解客戶如何部署及使用檢視器控制項，未來開發就可以專注於為客戶實現最大價值的改善。

如需 Microsoft SQL Server 2016 版本及任何其他產品和服務中使用者資料收集與使用方式的說明，請參閱這份 [Microsoft 提供的隱私權聲明](https://www.microsoft.com/EN-US/privacystatement/SQLServer/Default.aspx)。

## <a name="opting-out-of-telemetry"></a>退出遙測

您可以透過 “EnableTelemetry” 以程式設計方式停用遙測。 做法是編輯裝載控制項的 .aspx 頁面

```
\<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
\</rsweb:ReportViewer>
```

或者，在轉譯控制項之前 (例如在裝載頁面的 Page_Load 呼叫中) 以程式設計方式停用。
    
```
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>另請參閱

[使用 WebForms ReportViewer 控制項](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[使用 ReportViewer 控制項整合 Reporting Services](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 



