---
title: "具有明確頂層的衍生階層 (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies [Master Data Services], derived hierarchies with explicit caps
- explicit hierarchies, derived hierarchies with explicit caps
- derived hierarchies, derived hierarchies with explicit caps
ms.assetid: 6a82ff66-c137-4757-99bb-787d189b4295
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 811aa84b91aa7c91aa56dbf231c2ef2d247ec015
ms.contentlocale: zh-tw
ms.lasthandoff: 09/07/2017

---
# <a name="derived-hierarchies-with-explicit-caps-master-data-services"></a>具有明確頂層的衍生階層 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，當明確階層的層級當做衍生階層的最上層使用時，稱為具有明確頂層的衍生階層。  
  
 明確階層必須是以衍生階層最上方之實體的相同實體為基礎。  
  
 在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 使用者介面 (UI) 中，您可以將明確階層拖曳至衍生階層最上方，以建立此階層類型。  
  
 ![mds_conc_explicit_cap_UI_structure](../master-data-services/media/mds-conc-explicit-cap-ui-structure.gif "mds_conc_explicit_cap_UI_structure")  
  
## <a name="derived-hierarchy-with-explicit-cap-example"></a>具有明確頂層的衍生階層範例  
 在這個範例中，明確階層中的成員是來自 Subcategory 實體。 在衍生階層中，最上層成員也是來自 Subcategory 實體。  
  
 ![mds_conc_explicit_cap_UI_example](../master-data-services/media/mds-conc-explicit-cap-ui-example.gif "mds_conc_explicit_cap_UI_example")  
  
 透過在衍生階層最上方使用明確階層，衍生階層會變得不完全。  
  
## <a name="rules"></a>規則  
  
-   具有明確頂層的衍生階層中不能有一個以上的明確階層。  
  
-   同一個明確階層可以做為多個衍生階層的端點。  
  
-   不能指派階層成員權限給具有明確頂層的衍生階層。 如果您個別指派權限給明確階層或衍生階層，此權限會同時影響這兩個階層。  
  
## <a name="related-tasks"></a>相關工作  
  
|工作描述|主題|  
|----------------------|-----------|  
|建立衍生階層。|[建立衍生階層 &#40;Master Data Services&#41;](../master-data-services/create-a-derived-hierarchy-master-data-services.md)|  
|建立明確階層。|[建立明確階層 &#40;Master Data Services&#41;](../master-data-services/create-an-explicit-hierarchy-master-data-services.md)|  
|刪除現有衍生階層。|[刪除衍生階層 &#40;Master Data Services&#41;](../master-data-services/delete-a-derived-hierarchy-master-data-services.md)|  
|||  
  
## <a name="related-content"></a>相關內容  
  
-   [衍生階層 &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md)  
  
-   [明確階層 &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
  

