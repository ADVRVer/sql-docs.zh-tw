---
title: BaseProperty 元素 (CSDLBI) |Microsoft 文件
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f1e14b3bcfe862083aa78d634ca20ecaa0f4dd5c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34040844"
---
# <a name="baseproperty-element-csdlbi"></a>BaseProperty 元素 (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  BaseProperty 元素為複雜類型，可做為其他元素的基底。  
  
 其屬性可以出現在資料行和量值中。  
  
## <a name="elements-and-attributes"></a>元素和屬性  
 下表列出定義 BaseProperty 元素的元素和屬性。  
  
|名稱|是否必要|說明|  
|----------|-----------------|-----------------|  
|Alignment|否|成員 (資料行、量值、導覽屬性、階層或層級) 的名稱，藉由實作 Member 類型所定義。|  
|FormatString|否|成員的顯示名稱。|  
|IsRightToLeft|否|布林值，指出欄位是否包含可由右至左讀取的文字。<br /><br /> 如果省略此屬性，則會使用 (模型的) 預設設定。|  
|SortDirection|否|值，指出一般的欄位值排序方式。 此屬性的內容是由 SortDirection 簡單類型定義。<br /><br /> 如果省略此屬性，排序方向是依據欄位的資料類型指派。|  
|單位|否|套用至欄位值以表示單位的符號。<br /><br /> 如果省略，則單位為未知。|  
  
## <a name="alignment-element"></a>Alignment 元素  
 此簡單類型會定義用於區分成員的命名格式。  
  
|Value|說明|  
|-----------|-----------------|  
|無|使用屬性名稱。|  
|內容|使用內送關聯性名稱。|  
|合併式|根據目前文法的規則，串連內送關聯性名稱和屬性名稱。|  
  
## <a name="sortdirection-element"></a>SortDirection 元素  
 此簡單類型會定義用於區分成員的命名格式。  
  
|Value|說明|  
|-----------|-----------------|  
|無|使用屬性名稱。|  
|內容|使用內送關聯性名稱。|  
|合併式|串連內送關聯性名稱和屬性名稱。|  
  
## <a name="see-also"></a>另請參閱  
 [了解表格式物件模型在相容性層級 1050年透過 1103](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
