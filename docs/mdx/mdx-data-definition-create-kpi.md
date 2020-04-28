---
title: CREATE KPI 語句（MDX） |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e2380f72fe8a5faf9dc5504e56941f724b1bd159
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "68098407"
---
# <a name="mdx-data-definition---create-kpi"></a>MDX 資料定義 - CREATE KPI


  建立關鍵效能指標 (KPI) KPI 是用來評估商務或狀況成就的計算集合，這些計算與 Cube 中的量值群組相關聯。  
  
## <a name="syntax"></a>語法  
  
```  
  
CREATE KPI CURRENTCUBE | <Cube Name>.KPI_Name AS KPI_Value  
   [,Property_Name = Property_Value, ...n]  
```  
  
## <a name="arguments"></a>引數  
 *KPI_Name*  
 提供 KPI 名稱的有效字串。  
  
 *KPI_Value*  
 傳回數值的有效多維度運算式 (MDX) 運算式。  
  
 *Property_Name*  
 提供 KPI 屬性名稱的有效字串。  
  
 *Property_Value*  
 定義 KPI 屬性值的有效純量運算式。  
  
## <a name="remarks"></a>備註  
 指定目前連接之 Cube 以外的 Cube 會導致發生錯誤。 因此，您應該使用 CURRENTCUBE 取代 Cube 名稱，來代表目前的 Cube。  
  
## <a name="kpi-properties"></a>KPI 屬性  
 下表列出所有 KPI 屬性。 這些屬性中沒有一個有預設值。 因此，在將特定值指派給 KPI 屬性前，針對該屬性的查詢將會傳回 null 值。  
  
|屬性識別碼|意義|  
|-------------------------|-------------|  
|GOAL|傳回數值的有效 MDX 運算式。|  
|狀態|傳回數值的有效 MDX 運算式。|  
|STATUS_GRAPHIC|定義將由用戶端應用程式所使用之一組相片影像的字串。|  
|TREND|傳回數值的有效 MDX 運算式。|  
|TREND_GRAPHIC|定義將由用戶端應用程式所使用之一組相片影像的字串。|  
|WEIGHT|傳回數值的有效 MDX 運算式。|  
|CURRENT_TIME_MEMBER|傳回時間維度之成員的有效 MDX 運算式。 CURRENT_TIME_MEMBER 會針對所有相對的時間函數設定參考點|  
|PARENT_KPI|指定父 KPI 名稱的字串。|  
|CAPTION|用戶端應用程式當做 KPI 標題使用的字串。|  
|DISPLAY_FOLDER|指定用戶端應用程式顯示之 KPI 所在顯示資料夾路徑的字串。 資料夾層級的分隔符號是由用戶端應用程式所定義。 針對所提供的工具和客戶[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]端，反斜線\\（）為層級分隔符號。 若要針對已定義的成員提供多個顯示資料夾，請使用分號 (;) 來分隔資料夾|  
|ASSOCIATED_MEASURE_GROUP|指定所有 MDX 計算應參考之量值群組名稱的字串。|  
  
 GOAL、STATUS 和 TREND 屬性的值是應在 -1 和 1 之間評估的 MDX 運算式。 不過，用戶端應用程式會定義這些屬性的實際值範圍。 當您使用所提供的工具和客戶[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]端來流覽 kpi 時，小於-1 的值會被視為-1，而大於1的值會被視為1。  
  
 STATUS_GRAPHIC 和 TREND_GRAPHIC 都是用戶端應用程式用來識別要顯示之影像正確集合的字串值。 這些字串也會定義顯示函數的行為。 此行為包括要顯示之狀態的數目 (這通常是奇數)，以及要用於這些每個狀態的影像。  
  
### <a name="kpi-graphics-in-sql-server-data-tools"></a>SQL Server 資料工具中的 KPI 圖形  
 在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，KPI 圖形可以有三個或五個狀態。 下表定義每個狀態的值。  
  
|KPI 圖形的狀態數目|這些狀態的值|  
|--------------------------------------|---------------------------|  
|3|不良 = -1 到 -0.5<br /><br /> OK =-0.4999 到0.4999<br /><br /> 良好 = 0.50 到 1|  
|5|不良 = -1 到 -0.75<br /><br /> 危險 = -0.7499 到 -0.25<br /><br /> 沒有問題 = -0.2499 到 0.2499<br /><br /> 上升 = 0.25 到 0.7499<br /><br /> 良好 = 0.75 到 1|  
  
> [!NOTE]  
>  對於反向量測計或反向狀態箭頭之類的某些圖形，範圍會被反轉。 也就是說，-1 為良好，而 1 為不良。  
  
 在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，KPI 圖形的名稱可以判斷圖形有三種還是五種狀態。 下表列出使用方式、名稱，以及與其 KPI 圖形[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]相關聯的狀態數目。  
  
|圖形的用法|KPI 圖形的名稱|狀態的數目|  
|--------------------|-------------------------|----------------------|  
|狀態|圖形|3|  
|狀態|號誌燈|3|  
|狀態|道路標誌|3|  
|狀態|量測計|3|  
|狀態|反向量測計|5|  
|狀態|溫度計|3|  
|狀態|圓柱|3|  
|狀態|笑臉|3|  
|狀態|變異箭頭|3|  
|趨勢|標準箭頭|3|  
|趨勢|狀態箭頭|3|  
|趨勢|反向狀態箭頭|5|  
|趨勢|笑臉|3|  
  
## <a name="see-also"></a>另請參閱  
 [DROP KPI 語句 &#40;MDX&#41;](../mdx/mdx-data-definition-drop-kpi.md)   
 [Mdx 資料定義語句 &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
