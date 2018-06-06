---
title: 移除轉譯延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 03/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: extensions
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
caps.latest.revision: 38
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 6dc0893d138261a1bb173d03edf2ebb4fd4636b6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="removing-a-rendering-extension"></a>移除轉譯延伸模組
  若要移除 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 轉譯延伸模組，只要從 rsreportserver.config 檔案 (位於 **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<執行個體名稱>\Reporting Services\ReportServer** 資料夾) 中移除轉譯延伸模組的 **Extension** 項目即可。 如果您已經為報表設計師以及報表伺服器建立項目，請同時從 [RSReportDesigner 設定檔](../../../reporting-services/report-server/rsreportdesigner-configuration-file.md)中移除 **Extension** 項目。 在移除組態資訊之後，轉譯延伸模組將無法再供元件使用。  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services 組態檔](../../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [實作轉譯延伸模組](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [轉譯延伸模組概觀](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)   
 [實作 IRenderingExtension 介面](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)   
 [延伸模組的安全性考量](../../../reporting-services/extensions/security-considerations-for-extensions.md)   
 [部署轉譯延伸模組](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
  
