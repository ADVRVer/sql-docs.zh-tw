---
title: 依行動報表中的資料行或資料列群組資料 | Reporting Services | Microsoft Docs
description: 在行動報表發行工具中，您可在許多圖表類型中依資料行或資料列組織資料。 本文說明以資料行或資料列結構化的資料。
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: b9ebd36c-a337-47ae-83e5-6c2f2144eb52
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d775b0346ce2838abeec4bebce55762afd3b0adc
ms.sourcegitcommit: ea0bf89617e11afe85ad85309e0ec731ed265583
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92907326"
---
# <a name="group-data-by-columns-or-rows-in-a-mobile-report--reporting-services"></a>依行動報表中的資料行或資料列群組資料 | Reporting Services
您可以在許多圖表類型中，使用 [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)]依資料行或資料列來組織資料。 請遵循下列逐步指示。

在時間圖表、總計圖表、圓形圖和漏斗圖中，您可以依資料列或資料行來組織資料。 
* 如果您想要比較資料表中的多個資料行，依資料行組織就會很有用。 
* 如果資料表中有一個資料行包含不同類別目錄的名稱，依資料列組織會更適當。 

下列步驟在 [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)] 中使用內含模擬資料的比較總計資料表，來描述在圖表中依資料列結構化資料與依資料行結構化資料之間的差異。  

1. 將 [比較總計圖表]  從 [配置]  索引標籤拖曳至設計介面，並放大圖表。

2. 選取 [資料]  索引標籤。您會看到 SimulatedTable 資料表包含一系列的資料行 **Metric1** 至 **Metric5** ，以及 **Comparison1** 至 **Comparison5** 。 

   ![行動報表資料群組資料行的螢幕擷取畫面。](../../reporting-services/mobile-reports/media/mobile-report-data-group-column.png)

3. 在 [資料屬性]  窗格中，[主要數列]  是 [SimulatedTable]  。 選取 [主要數列]  旁邊方塊中的箭頭，您會看到 **Metric1** 至 **Metric5** 處於選取狀態。

   ![[主要數列] 旁邊選項的螢幕擷取畫面。](../../reporting-services/mobile-reports/media/mobile-report-properties-columns.png)

   同樣地，您會看到 [比較數列]   -- **Comparison1** 至 **Comparison5** 處於選取狀態。
   
4. 選取 [預覽]  。

   ![比較總計圖表預覽的螢幕擷取畫面。](../../reporting-services/mobile-reports/media/mobile-report-chart-by-columns.png)

   圖表中的每個橫條各代表資料表中的一個資料行。 較粗的橫條是 [矩陣] 資料行，較細的橫條是 [比較] 資料行。

5. 選取左上角的上一頁箭頭，即可離開預覽模式。

6. 在 [配置]  索引標籤的 [視覺屬性]  窗格中，將 [資料結構]  從 [循資料行]  變更為 [循資料列]  。  

7. 選取 [資料]  索引標籤。現在 SimulatedTable 資料表會包含 [類別目錄]  、[矩陣]  和 [比較]  資料行，以及類別目錄 A 至 E。 

   ![行動報表資料群組資料列的螢幕擷取畫面。](../../reporting-services/mobile-reports/media/mobile-report-data-group-rows.png)

8.  在 [資料屬性]  窗格中，現在會有 [類別目錄資料行] 方塊，其中列出 SimulatedTable 中的 [類別目錄] 資料行。 在 [主要數列] 中，您可以挑選使用哪些資料行來顯示值。 根據預設， [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)] 會選取 Metric1 至 Metric5 作為主要數列，並選取 Comparison1 至 Comparison5 作為比較數列。 

    ![[比較數列] 旁邊選項的螢幕擷取畫面。](../../reporting-services/mobile-reports/media/mobile-report-properties-rows.png)

9. 選取 [預覽]  。

   ![已更新的比較總計圖表預覽螢幕擷取畫面。](../../reporting-services/mobile-reports/media/mobile-report-chart-by-rows.png)

   現在，圖表中的每個橫條各代表 [類別目錄] 資料行中每個類別目錄的值。

### <a name="see-also"></a>另請參閱
* [Reporting Services 行動報表中的視覺效果](../../reporting-services/mobile-reports/add-visualizations-to-reporting-services-mobile-reports.md)
