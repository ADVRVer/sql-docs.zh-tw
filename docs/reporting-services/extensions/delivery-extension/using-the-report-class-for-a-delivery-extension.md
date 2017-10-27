---
title: "使用傳遞延伸模組的報表類別 |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- delivery extensions [Reporting Services], report information
- Report class
ms.assetid: 1145ac63-eafd-452a-82af-16f85b1676dd
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 2cbf3f1a1ffeb702551a2aa0ff94134867cb1786
ms.contentlocale: zh-tw
ms.lasthandoff: 08/12/2017

---
# <a name="using-the-report-class-for-a-delivery-extension"></a>使用傳遞延伸模組的報表類別
  <xref:Microsoft.ReportingServices.Interfaces.Report> 類別代表報表伺服器資料庫中的報表。 任何訂閱都與特定報表相關聯。 報表包含在通知中。 您的傳遞延伸模組可以使用屬於通知一部分的 <xref:Microsoft.ReportingServices.Interfaces.Report> 物件來轉譯報表。 <xref:Microsoft.ReportingServices.Interfaces.Report> 物件也包含報表特定屬性，例如在報表伺服器上的報表 URL 以及報表名稱。 這些屬性全部都可以做為傳遞提供者的一部分。  
  
 <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> 類別的 <xref:Microsoft.ReportingServices.Interfaces.Report>方法可用以轉譯報表。 <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> 方法會傳回一或多個 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 物件的陣列，全部加起來即可構成單一轉譯報表。 第一個 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 物件是轉譯報表。 任何其他 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 物件都是必須連同報表資料一起傳遞的資源 (例如，HTML 檔案與相關聯的影像)。 是單一資料流轉譯延伸模組的轉譯延伸模組 (IMAGE、PDF、MHTML 和 Excel) 只會在陣列中傳回一個 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 物件。  
  
 包含報表資料流的 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 物件，可以包括在傳遞中。  
  
 如需如何使用的範例<xref:Microsoft.ReportingServices.Interfaces.Report>類別，請參閱[SQL Server Reporting Services 產品範例](http://go.microsoft.com/fwlink/?LinkId=177889)  
  
## <a name="see-also"></a>另請參閱  
 [實作傳遞延伸模組](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services 延伸模組程式庫](../../../reporting-services/extensions/reporting-services-extension-library.md)   
 [使用傳遞延伸模組的 RenderedOutputFile 類別](../../../reporting-services/extensions/delivery-extension/using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
  
  

