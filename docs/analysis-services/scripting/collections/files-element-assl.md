---
title: "檔案元素 (ASSL) |Microsoft 文件"
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
- Files Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Files
helpviewer_keywords:
- Files element
ms.assetid: 8a1327cb-1f60-42a7-b8ef-213d45a63e55
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4bc56c3401a4e665e0ea62c3d003bfd0b4e75539
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="files-element-assl"></a>Files 元素 (ASSL)
  包含集合[檔案](../../../analysis-services/scripting/objects/file-element-assl.md)構成項目[ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Assembly xsi:type="ClrAssembly">  
   ...  
   <Files>  
      <File xsi:type="ClrAssemblyFile">...</File>  
   </Files>  
   ...  
</Assembly>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|無|  
|預設值|無|  
|基數|1-1：只出現一次的必要元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[組件](../../../analysis-services/scripting/objects/assembly-element-assl.md)型別的[ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)|  
|子元素|[檔案](../../../analysis-services/scripting/objects/file-element-assl.md)型別的[ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)|  
  
## <a name="remarks"></a>備註  
 分析管理物件 (AMO) 物件模型中的對應元素是<xref:Microsoft.AnalysisServices.ClrAssemblyFileCollection>。  
  
## <a name="see-also"></a>另請參閱  
 [Server 元素 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Database 元素 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Assemblies 元素 &#40;ASSL &#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [資料元素 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/data-element-assl.md)   
 [DataBlock 資料類型 &#40;ASSL &#41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Blocks 元素 &#40;ASSL &#41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Block 元素 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [ComAssembly 資料類型 &#40;ASSL &#41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [集合 &#40;ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  

