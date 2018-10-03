---
title: 排序轉換編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sorttransformation.f1
helpviewer_keywords:
- Sort Transformation Editor
ms.assetid: 8ae23970-49a9-4d6d-9f15-c7074783347c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d57129a0997093aa351b83b09f87ee7d38bb2a25
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178308"
---
# <a name="sort-transformation-editor"></a>排序轉換編輯器
  使用 **[排序轉換編輯器]** 對話方塊，即可選取要排序的資料行、設定排序順序和指定是否要移除重複的項目。  
  
 若要深入了解排序轉換，請參閱＜ [Sort Transformation](data-flow/transformations/sort-transformation.md)＞。  
  
## <a name="options"></a>選項。  
 **可用的輸入資料行**  
 使用核取方塊來指定要排序的資料行。  
  
 **名稱**  
 檢視每個可用輸入資料行的名稱。  
  
 **通過**  
 指出排序的輸出中是否包含資料行。  
  
 **輸入資料行**  
 從每個資料列的可用輸入資料行清單中選取。 您的選擇會反映在 **[可用的輸入資料行]** 資料表的核取方塊選擇中。  
  
 **輸出別名**  
 輸入每一個輸出資料行的別名。 預設是輸入資料行的名稱；但是，您可以選擇任何唯一的、描述性名稱。  
  
 **排序類型**  
 指出是要依遞增或遞減的順序來排序。  
  
 **排序次序**  
 指出資料行的排序順序。 必須以手動的方式為每個資料行設定。  
  
 **比較旗標**  
 如需字串比較選項的相關資訊，請參閱 [比較字串資料](data-flow/comparing-string-data.md)。  
  
 **移除排序值重複的資料列**  
 指出轉換是否將重複的資料列複製到轉換輸出，或依據指定的字串比較選項為所有重複的資料列建立單一項目。  
  
## <a name="see-also"></a>另請參閱  
 [Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
