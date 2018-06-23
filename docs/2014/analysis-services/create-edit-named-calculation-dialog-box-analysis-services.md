---
title: 建立編輯具名計算對話方塊 (Analysis Services) |Microsoft 文件
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
- sql12.asvs.dsveditor.createnamedcalculation.f1
helpviewer_keywords:
- Named Calculation dialog box
ms.assetid: 66fb30ae-f5c5-4bfc-80ca-8c8a3a9bb30d
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 007fce8fae62df381629b4daa1b6ef0c00d781bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36022296"
---
# <a name="create-edit-named-calculation-dialog-box-analysis-services"></a>建立編輯具名計算對話方塊 (Analysis Services)
  使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的 [建立/編輯具名計算] 對話方塊，即可定義或修改資料來源檢視中之資料表的具名計算。 您可以執行下列動作來顯示 [建立/編輯具名計算] 對話方塊：  
  
-   在 [資料來源檢視設計師] 的 [工具列] 窗格中，按一下 [新增具名計算]。  
  
-   在 [資料來源檢視設計師] 的 [資料表] 或 [圖表] 窗格中，以滑鼠右鍵按一下資料表，然後選取 [新增具名計算]。  
  
-   在 [資料來源檢視設計師] 的 [圖表] 窗格中，以滑鼠右鍵按一下具名計算的名稱，然後選取 [編輯具名計算]。  
  
## <a name="options"></a>選項。  
 **資料行名稱**  
 輸入具名計算的名稱。  
  
 **說明**  
 輸入具名計算的選擇性描述。  
  
 **運算式**  
 輸入傳回純量值的有效 SQL 運算式。 運算式會傳送給提供者，並在下列運算式中進行驗證：  
  
```  
SELECT <Table Name in Data Source>.* , <Expression> AS <Column Name> FROM <Table Name in Data Source>AS <Table Name in Data Source View>  
```  
  
 運算式可以透過子 SELECT 陳述式來包含其他資料表的參考。 如果運算式在 SELECT 陳述式中需要括號，則必須在輸入的運算式頭尾加上括號。  
  
## <a name="see-also"></a>另請參閱  
 [Analysis Services Designers and Dialog Boxes&#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [資料來源檢視設計師&#40;Analysis Services-多維度資料&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  