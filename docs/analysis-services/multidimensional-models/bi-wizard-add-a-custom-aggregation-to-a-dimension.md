---
title: "將自訂彙總加入維度 |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], custom aggregations
- aggregations [Analysis Services], custom
- unary operators
- custom aggregations [Analysis Services]
ms.assetid: 3199a6c2-a06d-47b9-bd1c-604dbb085318
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 63ad6f1d9e72fae70997c87aca194f7437c62d07
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="bi-wizard---add-a-custom-aggregation-to-a-dimension"></a>BI 精靈-將自訂彙總加入維度中
  將自訂彙總增強功能加入至 Cube 或維度中，以不同的一元運算子取代與維度成員相關聯的預設彙總。 此增強功能指定維度資料表中的一元運算子資料行，它定義父子式階層中的成員積存。 一元運算子是在父子式階層的父屬性上作用。  
  
> [!NOTE]  
>  只有以現有的資料來源為基礎的維度，才可使用自訂彙總。 對於沒有使用資料來源建立的維度，在加入自訂彙總之前，您必須執行結構描述產生精靈來建立資料來源檢視。  
  
 若要加入自訂彙總，您可以使用商業智慧精靈，並選取 **[選擇增強功能]** 頁面上的 **[指定一元運算子]** 選項。 此精靈會引導您完成一些步驟，來選取您要套用自訂彙總的維度及識別自訂彙總。  
  
> [!NOTE]  
>  在執行商業智慧精靈來加入自訂彙總之前，請確定您要增強的維度有包含父子屬性階層。 如需詳細資訊，請參閱 [父子式維度](../../analysis-services/multidimensional-models/parent-child-dimension.md)。  
  
## <a name="selecting-a-dimension"></a>選取維度  
 在精靈的第一個 **[指定一元運算子]** 頁面上，您可以選取要套用自訂彙總的維度。 自訂彙總加入至這個選取的維度之後，會導致維度變更。 包含選取之維度的所有 Cube，都會繼承這些變更。  
  
## <a name="adding-custom-aggregation-unary-operator"></a>加入自訂彙總 (一元運算子)  
 在第二個 **[指定一元運算子]** 頁面上，您可以指定自訂彙總的父屬性，以及維度資料表中供一元運算子使用的來源資料行。 **[父屬性]** 列出其 **Usage** 屬性已設為 **Parent**的屬性。 如果有一個以上的父屬性，請選擇對應到您要使用之父子式階層關聯性的父屬性。 如果沒有列出父屬性，表示該維度不含有效的父子式階層。  
  
 在 **[來源資料行]**中，您可以選取包含一元運算子的字串資料行。 (此選取項目設定父屬性上的 **UnaryOperatorColumn** 屬性)。維度資料表也應該有指定一元積存運算子的字串資料行。 此資料行的字串值應包含有效彙總運算子。 如果資料列空白，會正常計算相對應的成員。 如果資料行中的公式無效，當擷取使用該成員的資料格值時，會發生執行階段錯誤。 如需詳細資訊，請參閱 [父子式維度中的一元運算子](../../analysis-services/multidimensional-models/parent-child-dimension-attributes-unary-operators.md)。  
  
  
