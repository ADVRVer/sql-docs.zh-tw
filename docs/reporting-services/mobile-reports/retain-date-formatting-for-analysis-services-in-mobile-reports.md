---
title: "保留日期格式為 Analysis Services 行動報表中 |Reporting Services |Microsoft 文件"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9a9a199-40e3-4381-b250-1b99fb83aa62
caps.latest.revision: 3
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0a4da31bb1ed09024c6278193e8011b5c7981922
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="retain-date-formatting-for-analysis-services-in-mobile-reports"></a>保留行動報表中 Analysis Services 的日期格式
在報表產生器中將量值加入共用資料集中，讓 [!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)] 資料來源中的日期在 [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)]中保留其資料類型。

[!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)] 查詢的預設傳回類型是字串。  在 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 報表產生器中建立資料集時，會使用字串類型，並將其儲存至伺服器。 

不過，當 JSON 資料表轉譯器處理資料集時，會將資料行的值讀取為字串，並轉譯字串。  接著， [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)] 提取資料表時，也只會看到字串。

在報表產生器中建立共用資料集時，此問題的因應措施是加入導出成員。 它適用於 [!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)] 多維度和表格式模型。

## <a name="create-a-measure-to-retain-a-date-field-data-type"></a>建立量值來保留日期欄位資料類型

1. 建立量值以保留有問題之日期欄位的值，然後在運算式欄位中，選擇日期的階層/層級，並附加 **.CurrentMember.MemberValue**。 例如：
 
   [Internet Sales].[Ship Date].CurrentMember.MemberValue
   
   ![ssas-calculated-member-report-builder](../../reporting-services/mobile-reports/media/ssas-calculated-member-report-builder.png)
   
2. 現在您可以將此導出成員附加至這組資料行，方法是將它從左下方的 [導出成員] 清單拖放至右邊的資料行方格。  

   ![ssas-query-designer-calculated-member-report-builder](../../reporting-services/mobile-reports/media/ssas-query-designer-calculated-member-report-builder.png) 
   
### <a name="see-also"></a>另請參閱

-  [Reporting Services 行動報表的資料](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md)
-  [準備 Reporting Services 行動報表資料](../../reporting-services/mobile-reports/prepare-data-for-reporting-services-mobile-reports.md)
