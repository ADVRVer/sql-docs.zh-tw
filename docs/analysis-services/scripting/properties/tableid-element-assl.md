---
title: "TableID 元素 (ASSL) |Microsoft 文件"
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
- TableID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TableID
helpviewer_keywords:
- TableID element
ms.assetid: 45fe7e23-b274-4bc2-be63-1a5bb6680f51
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 89a10083cd42179ad72af682e337c67691dff491
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="tableid-element-assl"></a>TableID 元素 (ASSL)
  包含資料表的識別碼 (ID) (從[DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)項目) 與父元素相關聯。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<ColumnBinding> <!-- or DSVTableBinding, RowBinding, IncrementalProcessingNotification -->  
   ...  
   <TableID>...</TableID>  
   ...  
</ColumnBinding>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|字串|  
|預設值|無|  
|基數|1-1：只出現一次的必要元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)， [DSVTableBinding](../../../analysis-services/scripting/data-type/dsvtablebinding-data-type-assl.md)， [IncrementalProcessingNotification](../../../analysis-services/scripting/objects/incrementalprocessingnotification-element-assl.md)， [RowBinding](../../../analysis-services/scripting/data-type/rowbinding-data-type-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 識別之資料表**TableID**必須在主控的物件 （維度或 cube） 繫結至資料來源。  
  
 對應至父系的項目**TableID**在 「 分析管理物件 (AMO) 物件模型是<xref:Microsoft.AnalysisServices.ColumnBinding>， <xref:Microsoft.AnalysisServices.DSVTableBinding>， <xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>，和<xref:Microsoft.AnalysisServices.RowBinding>。  
  
## <a name="see-also"></a>另請參閱  
 [屬性 &#40;ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

