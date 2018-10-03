---
title: 聯結對話方塊 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- vdt.ppg.joinline
- vdtsql.chm:69638
ms.assetid: 0d9516bb-4ad3-4fcf-bb77-93474dea698f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8314b283bbb28752e98e5c7e34e2f1625cf8827b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087058"
---
# <a name="join-dialog-box-visual-database-tools"></a>聯結對話方塊 (Visual Database Tools)
  使用此對話方塊可指定聯結資料表的選項。 若要存取此對話方塊，請在 [設計] 窗格中選取聯結線 (Join Line)。 然後，在 [屬性] 視窗中按一下 [聯結條件及類型]，並按一下顯示在屬性右邊的省略符號 (**…**)。  
  
 依照預設，是使用根據包含聯結資料行中符合資訊資料列來建立結果集的內部聯結，將關聯資料表聯結在一起。 藉由設定 [聯結] 對話方塊中的選項，可以根據不同的運算子指定聯結，也可以指定外部聯結。  
  
 如需聯結資料表的詳細資訊，請參閱[使用聯結查詢 &#40;Visual Database Tools&#41;](visual-database-tools.md)。  
  
## <a name="options"></a>選項。  
  
|**詞彙**|**定義**|  
|--------------|--------------------|  
|**Table**|聯結中相關資料表或資料表值物件的名稱。 不能在這裡變更資料表的名稱 — 此資訊只用於顯示資訊。|  
|**資料行**|用於聯結資料表的資料行名稱。 運算子清單中的運算子會指定各資料行中資料之間的關係。 不能在這裡變更資料行的名稱 — 此資訊只用於顯示資訊。|  
|**運算子**|指定用於關聯聯結資料行的運算子。 若要指定等於 (=) 之外的運算子，請從清單中選取。 關閉屬性頁時，您選取的運算子會出現在聯結線的菱形圖中，如下所示：<br /><br /> ![Visual Database Tools 圖示](../../database-engine/media//dv3wbii.gif "Visual Database Tools 圖示")|  
|**中的所有資料列\<table1 >**|指定輸出中顯示左邊資料表裡全部的資料列，即使右邊資料表中沒有對應的符合也一樣。 右邊資料表中沒有符合資料的資料行會顯示為 null。 選擇此選項就等於在 SQL 陳述式中指定 LEFT OUTER JOIN。|  
|**中的所有資料列\<table2 >**|指定輸出中顯示右邊資料表裡全部的資料列，即使左邊資料表中沒有對應的符合也一樣。 左邊資料表中沒有符合資料的資料行會顯示為 null。 選擇此選項就等於在 SQL 陳述式中指定 RIGHT OUTER JOIN。|  
  
 同時選取**中的資料列\<table1 >** 並**中的所有資料列\<table2 >** 相當於指定的 SQL 陳述式中的 FULL OUTER JOIN。  
  
 選取某個選項建立外部聯結時，聯結線中的菱形圖就會改變，以指示聯結為左邊外部、右邊外部或完整外部聯結。  
  
> [!NOTE]  
>  「左邊」和「右邊」這兩個字不一定對應到 [圖表] 窗格中的資料表位置。 「左邊」指的是在 SQL 陳述式中名稱出現在關鍵字 JOIN 左邊的資料表，「右邊」指的是名稱出現在關鍵字 JOIN 右邊的資料表。 如果在 [圖表] 窗格中移動資料表，則不必變更資料表是左邊或右邊的考量。  
  
## <a name="see-also"></a>另請參閱  
 [使用聯結查詢&#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
