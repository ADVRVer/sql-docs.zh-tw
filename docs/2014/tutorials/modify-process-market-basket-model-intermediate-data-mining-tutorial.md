---
title: 修改及處理購物籃模型 （中繼資料採礦教學課程） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b6019413-aebd-4ff7-831a-644572ad88b1
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f1f0fe6899be3f9828a8ba9d91f2c9abf7ba48b6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246118"
---
# <a name="modifying-and-processing-the-market-basket-model-intermediate-data-mining-tutorial"></a>修改及處理購物籃模型 (中繼資料採礦教學課程)
  處理您所建立的關聯採礦模型之前，您必須變更兩個參數的預設值：*支援*並*機率*。  
  
-   *支援*定義才會視為有效的規則必須存在的案例百分比。 您將會指定，至少必須在百分之 1 的案例中找到規則。  
  
-   *機率*定義必須關聯的方式可能會被視為有效之前。 您將會考量機率至少百分之 10 的任何關聯。  
  
 增加或減少支援與機率的效果的相關資訊，請參閱[Microsoft 關聯分析演算法技術參考](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)。  
  
 您已定義的結構和參數後**關聯**採礦模型，您會處理此模型。  
  
### <a name="to-adjust-the-parameters-of-the-association-model"></a>若要調整關聯模型的參數  
  
1.  開啟**採礦模型**資料採礦設計師 索引標籤。  
  
2.  以滑鼠右鍵按一下**關聯**的方格中選取與設計工具中的資料行**以開啟 演算法參數的 設定演算法參數** 對話方塊。  
  
3.  在 **值**資料行**演算法參數**對話方塊方塊中，設定下列參數：  
  
     MINIMUM_PROBABILITY = 0.1   
  
     MINIMUM_SUPPORT = 0.01  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-process-the-mining-model"></a>若要處理採礦模型  
  
1.  在 **採礦模型**功能表[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]，選取**處理採礦結構和所有模型。**  
  
2.  警告訊息，詢問您是否想要建置和部署專案，按一下**是**。  
  
     **處理採礦結構-關聯**對話方塊隨即開啟。  
  
3.  按一下 **[執行]**。  
  
     **處理進度**對話方塊會開啟以顯示模型處理的相關資訊。 處理新的結構和模型可能需要花一些時間。  
  
4.  已完成處理之後，請按一下**關閉**以結束**處理進度** 對話方塊。  
  
5.  按一下 [**關閉**以結束**處理採礦結構-關聯**] 對話方塊。  
  
## <a name="next-task-in-lesson"></a>本課程的下一項工作  
 [探索購物籃模型&#40;中繼資料採礦教學課程&#41;](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>另請參閱  
 [處理需求和考量&#40;資料採礦&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
