---
title: RelationalDataSource 資料類型 (ASSL) |Microsoft 文件
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9046573e26d7e0c53e5cce513fcfce43654af989
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="relationaldatasource-data-type-assl"></a>RelationalDataSource 資料類型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  定義衍生的資料類型，表示[DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md)關聯式資料來源為基礎的項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<RelationalDataSource>  
   <!-- Child elements are only those inherited from DataSource -->  
</RelationalDataSource>  
```  
  
## <a name="data-type-characteristics"></a>資料類型特性  
  
|特性|說明|  
|--------------------|-----------------|  
|基底資料類型|[DataSource](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)|  
|衍生資料類型|無|  
  
## <a name="data-type-relationships"></a>資料類型關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|無|  
|子元素|無|  
|衍生的元素|[資料來源](../../../analysis-services/scripting/objects/datasource-element-assl.md)([DataSources](../../../analysis-services/scripting/collections/datasources-element-assl.md)集合[資料庫](../../../analysis-services/scripting/objects/database-element-assl.md))|  
  
## <a name="remarks"></a>備註  
 分析管理物件 (AMO) 物件模型中的對應元素是<xref:Microsoft.AnalysisServices.RelationalDataSource>。  
  
## <a name="see-also"></a>另請參閱  
 [Analysis Services 指令碼語言 XML 資料類型 & #40;ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
