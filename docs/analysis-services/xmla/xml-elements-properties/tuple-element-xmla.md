---
title: "Tuple 元素 (XMLA) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Tuple Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.tuple
- urn:schemas-microsoft-com:xml-analysis#Tuple
- http://schemas.microsoft.com/analysisservices/2003/engine#Tuple
helpviewer_keywords:
- Tuple element
ms.assetid: d65aba10-55e1-49c1-81bc-0756c39c0da2
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 11a9d3b633e680154787615c04ee1f08b65b8139
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="tuple-element-xmla"></a>Tuple 元素 (XMLA)
  包含 [Tuples](../../../analysis-services/xmla/xml-elements-properties/tuples-element-xmla.md) 父元素所包含之 [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) 元素的集合。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Tuples>  
   <Tuple>  
      <Member>...</Member>  
   </Tuple>  
   ...  
</Tuples>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|無|  
|預設值|無|  
|基數|0-n：出現一次以上的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[Tuple](../../../analysis-services/xmla/xml-elements-properties/tuples-element-xmla.md)|  
|子元素|[成員](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
  
## <a name="remarks"></a>備註  
 當用戶端應用程式將 **AxisFormat** 屬性設為 *TupleFormat* 時，軸就會表示成 Tuple 集合。 每個 **Axis** 元素都包含代表該軸上 Tuple 集合的 **Tuples** 元素。 每個 Tuple 都會使用包含該軸上每個階層之 **Member** 元素的 **Tuple** 元素來表示。  
  
## <a name="example"></a>範例  
 下列範例將說明當用戶端指定 *TupleFormat* 或 *CustomFormat* 給 **AxisFormat** XMLA 屬性時，**Tuple** 元素的結構 (假設軸具有下列成員的話)：  
  
|||||  
|-|-|-|-|  
|**時間**階層|1999|1999|2000|  
|**類別目錄**階層|實際|預算|預算|  
  
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
 [屬性 &#40;XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
