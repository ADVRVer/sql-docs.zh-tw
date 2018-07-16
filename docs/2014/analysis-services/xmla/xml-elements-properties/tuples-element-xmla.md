---
title: Tuples 元素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Tuples Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Tuples
- microsoft.xml.analysis.tuples
- urn:schemas-microsoft-com:xml-analysis#Tuples
helpviewer_keywords:
- Tuples element
ms.assetid: 5494bbaa-c1aa-43fa-b3e0-83befb2bccdd
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5e5f6f1dbddea4e5e962d30f352c254b0f2a7a80
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37254590"
---
# <a name="tuples-element-xmla"></a>Tuples 元素 (XMLA)
  包含一組[Tuple](tuple-element-xmla.md)物件[軸](axis-element-xmla.md)使用的項目[MDDataSet](../xml-data-types/mddataset-data-type-xmla.md)所傳回的資料類型[Execute](../xml-elements-methods-execute.md)方法。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Axis>  
   ...  
   <Tuples>  
      <Tuple>...</Tuple>  
   </Tuples>  
   ...  
</Axis>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|無|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[Axis](axis-element-xmla.md)|  
|子元素|[元組](tuple-element-xmla.md)|  
  
## <a name="remarks"></a>備註  
 當用戶端應用程式設定`AxisFormat`屬性，以*TupleFormat*，軸就會表示為一組 tuple。 每個 `Axis` 元素都包含代表該軸上 Tuple 集合的 `Tuples` 元素。 每個 tuple 由使用`Tuple`包含的項目[成員](member-element-xmla.md)軸上每個階層中的項目。  
  
## <a name="example"></a>範例  
 下列範例說明的結構`Tuples`時用戶端指定的項目*TupleFormat*或是*CustomFormat*的`AxisFormat`XML for Analysis (XMLA) 屬性假設軸具有下列成員：  
  
|||||  
|-|-|-|-|  
|`Time` 階層|1999|1999|2000|  
|`Category` 階層|實際|預算|預算|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <Tuples>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
      </Tuples>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>另請參閱  
 [屬性&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
