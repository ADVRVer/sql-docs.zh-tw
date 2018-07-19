---
title: 定義參考的關聯性和參考關聯性屬性 |Microsoft 文件
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e3fe03648977cd15bb59a7e24290cf441967b702
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34027548"
---
# <a name="define-a-referenced-relationship-and-referenced-relationship-properties"></a>定義參考的關聯性及參考的關聯性屬性
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  參考維度關聯性是在 Cube 設計師的 [維度使用方式] 索引標籤上定義的。 透過指定下列項目即可定義參考維度關聯性：  
  
-   要聯結的中繼維度。 這可以是一般維度或另一個參考維度。  
  
-   在量值群組方面，定義可用於彙總之維度最低層級的參考維度屬性。  
  
-   對應到參考維度屬性之中繼維度中的 (外部索引鍵) 屬性。  
  
 請注意，將參考維度連結到事實資料表的資料行 (通常是參考維度中的索引鍵屬性)，在中繼維度中也必須定義為屬性。 當您建立參考維度的鏈結時，請從在鏈結的第一個維度和量值群組之間建立一般關聯性開始。 然後依序建立每一個額外的參考關聯性。 只有在維度與量值群組之間具有現有關聯性時，才可建立該維度的參考關聯性。  
  
 當您建立參考維度關聯性時，依預設會具體化維度屬性連結。 在處理期間，具體化維度屬性連結會造成事實資料表與每個資料列的參考維度之間的連結值，在維度的 MOLAP 結構中進行具體化或儲存。 這對於處理效能和儲存體需求會有些許影響，但可增加查詢效能。  
  
 在參考維度中，識別在參考維度與對應到維度之主資料表的量值群組之間定義關聯性的屬性，即可指定資料粒度。 當多個參考維度鏈結在一起時，參考是定義從最外層維度到量值群組的關聯性。  
  
  
