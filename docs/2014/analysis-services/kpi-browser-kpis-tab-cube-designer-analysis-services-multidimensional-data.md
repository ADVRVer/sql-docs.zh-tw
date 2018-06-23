---
title: KPI 瀏覽器 （Kpi 索引標籤，Cube 設計工具） (Analysis Services-多維度資料) |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.cubeeditor.kpibrowserpane.f1
ms.assetid: 2f61bde6-e6ec-4511-8645-c272374014ad
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 32373127f72dae058a80712cec564af7dffca45e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36133133"
---
# <a name="kpi-browser-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a>KPI 瀏覽器 (KPI 索引標籤，Cube 設計師) (Analysis Services - 多維度資料)
  在 Cube 設計師中，使用 [KPI] 索引標籤的 [KPI 瀏覽器] 窗格，即可檢視和測試關鍵效能指標 (KPI) 的結果。 瀏覽之前，KPI 必須先部署至 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體。  
  
> [!NOTE]  
>  此窗格只會顯示在瀏覽器檢視中。  
  
## <a name="options"></a>選項。  
 **Subcube 方格**  
 這可用來定義 Subcube 和限制 [結果] 窗格中顯示的 KPI 結果。 方格包含下列資料行：  
  
 **Dimension**  
 選取要套用此篩選的維度。  
  
 **Hierarchy**  
 選取要套用此篩選的階層。  
  
 **[運算子]**  
 選取運算子，定義 [篩選運算式] 中的運算式如何套用至所選取階層。 下表描述可用的運算子。  
  
|ReplTest1|描述|  
|-----------|-----------------|  
|**等於**|結果會限制為 **[篩選運算式]** 中定義的集合。|  
|**不等於**|結果會限制為 **[篩選運算式]** 中定義之集合所排除的成員。|  
|**In**|結果會限制為 **[篩選運算式]** 中選擇的命名集。|  
|**不能在**|結果會限制為 **[篩選運算式]** 中選擇之命名集所排除的成員。|  
|**包含**|結果會限制為成員名稱中包含 **[篩選運算式]** 中的字串之成員。|  
|**開頭為**|結果會限制為成員名稱是以 **[篩選運算式]** 中的字串開頭之成員。|  
|**範圍 （內含）**|結果會限制為 **[篩選運算式]** 中選擇的範圍。|  
|**範圍 （獨佔）**|結果會限制為 **[篩選運算式]** 中選擇之範圍所排除的成員。|  
|**MDX**|結果會限制為 [篩選運算式] 中的多維度運算式 (MDX) 運算式集合。|  
  
 **篩選運算式**  
 鍵入要由 [運算子] 評估的運算式，以限制要瀏覽的 KPI 結果。  
  
> [!NOTE]  
>  此欄位是一個動態資料輸入元素，外觀會變更以反映選取之運算子所需要的資料類型。  
  
 **結果方格**  
 依據 [篩選方格] 中定義的篩選，顯示 KPI 的評估值、目標、狀態及趨勢。 方格包含下列資料行：  
  
 **顯示結構**  
 顯示 Cube 包含的 KPI，並根據每一個 KPI 的 [顯示資料夾] 或 [父 KPI] 值來組織階層。  
  
 **ReplTest1**  
 顯示 KPI 的值。  
  
 **目標**  
 顯示 KPI 的目標值。  
  
 **狀態**  
 顯示 KPI 的狀態圖形。  
  
 **趨勢**  
 顯示 KPI 的趨勢圖形。  
  
 **Weight**  
 顯示 KPI 的加權因數。  
  
 **（描述）**  
 如果有提供 KPI 的描述，則顯示資訊圖示。  
  
 將游標停留在資訊圖示上，即可顯示 KPI 的工具提示 (包含描述)。  
  
> [!NOTE]  
>  如果在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體上計算 KPI 時發生錯誤，此選項就會顯示錯誤的資訊。  
  
## <a name="see-also"></a>另請參閱  
 [Kpi &#40;Cube 設計師&#41; &#40;Analysis Services-多維度資料&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md)  
  
  