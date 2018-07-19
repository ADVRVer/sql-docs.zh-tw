---
title: 伺服器屬性 (執行頁面) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: tools
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.serverproperties.execution.f1
ms.assetid: 53b77db1-b013-4dac-82dd-30c0de276639
caps.latest.revision: 32
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: c37ea4f28191e0b78977e4e7f2fb3bad102547cc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "33031935"
---
# <a name="server-properties-execution-page"></a>伺服器屬性 (執行頁面)
  使用此頁面，即可設定報表執行的逾時值。 此值適用於由目前報表伺服器執行個體處理的所有報表。 您可以針對個別報表覆寫此值。 您所指定的值必須配合在報表伺服器上進行的所有報表處理，再加上報表伺服器擷取報表中所使用的資料時，於資料庫伺服器上執行的查詢處理。  
  
 若要開啟此頁面，請啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、連接至報表伺服器執行個體、以滑鼠右鍵按一下報表伺服器名稱，然後選取 [屬性]。 按一下 **[執行]** ，即可開啟此頁面。  
  
## <a name="options"></a>選項。  
 **執行報表時，不要計算逾時值**  
 讓報表伺服器完成報表處理不受時間限制。  
  
 **限制報表僅能執行下列秒數**  
 設定報表執行的時間條件約束。 要求報表時，系統就會開始計算時間週期。 如果報表尚未處理完畢而時間週期已結束，報表伺服器就會取消此處理序，以及對外部資料來源的所有同處理序查詢。  
  
## <a name="see-also"></a>另請參閱  
 [設定報表伺服器屬性 &#40;Management Studio&#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [連接至 Management Studio 中的報表伺服器](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [設定報表處理屬性](../../reporting-services/report-server/set-report-processing-properties.md)   
 [設定報表和共用資料集處理的逾時值 &#40;SSRS&#41;](../../reporting-services/report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)   
 [Management Studio F1 說明中的報表伺服器](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)  
  
  
