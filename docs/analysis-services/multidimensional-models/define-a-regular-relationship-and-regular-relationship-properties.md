---
title: "定義一般關聯性及一般關聯性內容 |Microsoft 文件"
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
- granularity attribute
- relationships [Analysis Services], regular relationships
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c9706dbe2c2faca9e5aa71ae8432ddf5dc2279a9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a>定義一般關聯性及一般關聯性屬性
  當您定義新的 Cube 維度或新的量值群組時，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會嘗試偵測是否有一般關聯性，然後將維度使用方式設定設為 [一般]。 在 Cube 設計師的 [維度使用方式] 索引標籤上，您可以檢視或編輯一般維度關聯性。  
  
 當您定義 Cube 維度與量值群組的關聯性時，會同時為該關聯性指定資料粒度屬性。 資料粒度屬性會針對該維度定義 Cube 中可用之詳細資料的最低層級，這通常是維度的索引鍵屬性。 然而，有時您可能會想要在特定量值群組中，將特定 Cube 維度的資料粒度設定為不同的資料粒度。 例如，如果您使用的是 [銷售配額] 或 [預算] 量值群組，則可能會想要將 [時間] 維度的資料粒度屬性設定為 [月] 屬性而不是 [日] 屬性。 當您將資料粒度屬性指定為索引鍵屬性以外的屬性時，則必須確定維度中的其他所有屬性都是透過屬性關聯性直接或間接連結至另一個屬性。 否則， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 將無法正確地彙總資料。  
  
  
