---
title: 檢閱彙總使用方式 （彙總設計精靈） |Microsoft 文件
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
- sql12.asvs.aggregationdesignwizard.reviewusage.f1
ms.assetid: 107ee872-3df2-4931-b56c-af11e38f6745
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5a26ea23dda5bba4813a9c5a99d797471124750d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36134514"
---
# <a name="review-aggregation-usage-aggregation-design-wizard"></a>檢閱彙總使用方式 (彙總設計精靈)
  使用 **[檢閱彙總使用方式]** 頁面，即可設定彙總使用方式設定。  
  
## <a name="options"></a>選項。  
 **預設值**  
 選取此選項，即可將屬性的彙總使用方式設定設為 Default。 透過使用這項設定，設計工具會根據屬性和維度的類型來套用預設規則。  
  
 `Full`  
 若要設定的彙總使用方式設定屬性來選取`Full`。 透過使用這項設定，Cube 的每個彙總都必須包含這個屬性或在屬性鏈結中較低的相關屬性。 `Full`屬性包含許多成員時，應該避免使用彙總使用方式設定。 如果針對多個屬性或具有許多成員的屬性指定，這項設定可能會讓彙總無法設計，因為大小過大。  
  
 **無**  
 選取此選項，即可將屬性的彙總使用方式設定設為 None。 透過使用這項設定，Cube 的任何彙總都無法包含這個屬性。  
  
 `Unrestricted`  
 若要設定的彙總使用方式設定屬性來選取`Unrestricted`。 透過使用這項設定，系統將不會對彙總設計師設定任何限制。不過，此屬性仍然必須經過評估，以便判斷它是否為重要的彙總候選。  
  
 **設定所有預設值**  
 選取此選項，即可將所有屬性的彙總使用方式設定都設為 Default。  
  
## <a name="see-also"></a>另請參閱  
 [彙總設計精靈 F1 說明](aggregation-design-wizard-f1-help.md)   
 [Analysis Services 精靈&#40;多維度資料&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  