---
title: 從採礦結構移除資料行 |Microsoft 文件
ms.custom: ''
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], columns
- removing columns
- deleting columns
- columns [data mining], mining structure columns
ms.assetid: 41073ffe-9351-416b-9f0c-62634bc213f9
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3828410392fc4f6577bd83d4e80ed1862a9ea24e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="remove-columns-from-a-mining-structure"></a>從採礦結構中移除資料行
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  在建立採礦結構之後，您可以使用資料採礦設計師，從採礦結構中移除資料行。 移除採礦結構資料行的原因可能包含下列：  
  
-   採礦結構包含某個資料行的多個複本並且您想要在模型中避免使用重複資料。  
  
-   資料應受到保護，但已啟用鑽研。  
  
-   資料未在模型化中使用並且不應處理。  
  
 從採礦結構中刪除資料行並不會在資料來源檢視或外部資料中變更該資料行，只刪除中繼資料。 但在您變更採礦結構中使用的資料行時，必須重新處理採礦結構和以它為基礎的所有模型。  
  
### <a name="to-remove-a-column-from-the-mining-structure"></a>若要從採礦結構中移除資料行  
  
1.  選取資料採礦設計師中的 **[採礦結構]** 索引標籤。  
  
2.  展開採礦結構的樹狀，以顯示所有資料行。  
  
3.  以滑鼠右鍵按一下您想要刪除的資料行，然後選取 [刪除]。  
  
4.  在 **[刪除物件]** 對話方塊中，按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [採礦結構工作和使用說明](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
