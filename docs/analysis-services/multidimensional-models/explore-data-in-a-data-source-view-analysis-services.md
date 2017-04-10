---
title: "在資料來源檢視中瀏覽資料 (Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "瀏覽資料 [Analysis Services]"
  - "資料來源檢視 [Analysis Services], 瀏覽資料"
  - "檢視來源資料"
ms.assetid: 2c922c35-fbcb-45b2-96b1-c7a846d8b419
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 34
---
# 在資料來源檢視中瀏覽資料 (Analysis Services)
  您可以在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的資料來源檢視設計師中使用 [瀏覽資料] 對話方塊，瀏覽資料來源檢視 (DSV) 中之資料表、檢視或具名查詢的資料。 當您在資料來源檢視設計師中瀏覽資料時，可以檢視選定資料表、檢視或具名查詢中每一個資料行的內容。 檢視實際內容可協助您判斷是否需要所有的資料行、是否需要具名計算來提高使用者易懂性和可用性，以及現有的具名計算或具名查詢是否會傳回預期的值。  
  
 若要檢視資料，您必須要有使用中連接來連接到資料來源或 DSV 中選定物件的來源。 資料表中的任何具名計算也會在查詢中傳送。  
  
 以表格式格式傳回的資料可進行排序和複製。 按一下資料行標題，即可依據該資料行重新排序資料列。 您也可以反白顯示方格中的資料，按下 Ctrl-C 將選取範圍複製到剪貼簿。  
  
 您也可以控制取樣方法和取樣計數。 預設會傳回前 5000 個資料列。  
  
## 瀏覽資料或變更取樣選項  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟含有您想在其中瀏覽資料之資料來源檢視的專案，或連接到包含此資料來源檢視的資料庫。  
  
2.  在方案總管中，展開 [資料來源檢視] 資料夾，然後按兩下資料來源檢視。  
  
3.  以滑鼠右鍵按一下包含您要檢視之資料的資料表、檢視或具名查詢，然後按一下 [瀏覽資料]。  
  
     資料來源檢視中的資料表、檢視或具名查詢之基礎資料來源為查詢，而且結果會出現在 [瀏覽 \<物件名稱> 資料表] 索引標籤中。  
  
4.  在 [瀏覽 \<物件名稱> 資料表] 工具列上，按一下**取樣選項**圖示。  
  
     **[資料瀏覽選項]** 對話方塊隨即開啟。 在這個對話方塊中，您可以指定取樣方法 (比預設取樣大小 5000 個資料列更多或更少)，或取樣計數。  
  
5.  依適當情況按一下 **[確定]** 或 **[取消]** 。  
  
6.  若要重新進行資料取樣，請按一下 [瀏覽 \<物件名稱> 資料表] 工具列上的 [重新進行資料取樣]。  
  
## 請參閱＜  
 [多維度模型中的資料來源檢視](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  