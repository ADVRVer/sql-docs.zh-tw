---
title: "TimeBinding 資料類型 (ASSL) |Microsoft 文件"
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
- TimeBinding Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TimeBinding
helpviewer_keywords:
- TimeBinding data type
ms.assetid: f3c06978-c181-4a73-9b57-8fc30358faab
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 32b8301a89ded8abbdee46941f5d905b991d14c1
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="timebinding-data-type-assl"></a>TimeBinding 資料類型 (ASSL)
  定義代表時間週期之繫結的衍生資料類型。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<TimeBinding>  
   <!-- The following elements extend Binding -->  
      <CalendarStartDate>...</CalendarStartDate>  
      <CalendarEndDate>...</CalendarEndDate>  
      <FirstDayOfWeek>...</FirstDayOfWeek>  
   <CalendarLanguage>...</CalendarLanguage>  
   <FiscalFirstMonth>...</FiscalFirstMonth>  
   <FiscalFirstDayOfMonth>...</FiscalFirstDayOfMonth>  
   <FiscalYearName>...</FiscalYearName>  
   <ReportingFirstMonth>...</ReportingFirstMonth>  
   <ReportingFirstWeekOfMonth>...</ReportingFirstWeekOfMonth>  
   <ReportingWeekToMonthPattern>...</ReportingWeekToMonthPattern>  
   <ManufacturingFirstMonth>...</ManufacturingFirstMonth>  
   <ManufacturingFirstWeekOfMonth>...</ManufacturingFirstWeekOfMonth>  
   <ManufacturingExtraMonthQuarter>...</ManufacturingExtraMonthQuarter>  
</TimeBinding>  
```  
  
## <a name="data-type-characteristics"></a>資料類型特性  
  
|特性|說明|  
|--------------------|-----------------|  
|基底資料類型|[繫結](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|衍生資料類型|無|  
  
## <a name="data-type-relationships"></a>資料類型關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|無|  
|子元素|[CalendarEndDate](../../../analysis-services/scripting/properties/calendarenddate-element-assl.md)， [CalendarLanguage](../../../analysis-services/scripting/properties/calendarlanguage-element-assl.md)， [CalendarStartDate](../../../analysis-services/scripting/properties/calendarstartdate-element-assl.md)， [FirstDayOfWeek](../../../analysis-services/scripting/properties/firstdayofweek-element-assl.md)， [FiscalFirstDayOfMonth](../../../analysis-services/scripting/properties/fiscalfirstdayofmonth-element-assl.md)， [FiscalFirstMonth](../../../analysis-services/scripting/properties/fiscalfirstmonth-element-assl.md)， [FiscalYearName](../../../analysis-services/scripting/properties/fiscalyearname-element-assl.md)， [ManufacturingExtraMonthQuarter](../../../analysis-services/scripting/properties/manufacturingextramonthquarter-element-assl.md)， [ManufacturingFirstMonth](../../../analysis-services/scripting/properties/manufacturingfirstmonth-element-assl.md)， [ManufacturingFirstWeekOfMonth](../../../analysis-services/scripting/properties/manufacturingfirstweekofmonth-element-assl.md)， [ReportingFirstMonth](../../../analysis-services/scripting/properties/reportingfirstmonth-element-assl.md)， [ReportingFirstWeekOfMonth](../../../analysis-services/scripting/properties/reportingfirstweekofmonth-element-assl.md)， [ReportingWeekToMonthPattern](../../../analysis-services/scripting/properties/reportingweektomonthpattern-element-assl.md)|  
|衍生的元素|請參閱[繫結](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>備註  
 如需有關**繫結**型別，包括之 Analysis Services 指令碼語言 (ASSL) 物件的資料表**繫結**型別和繼承階層架構的**繫結**類型，請參閱[繫結資料類型 &#40;ASSL &#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 如需 ASSL 中資料繫結的概觀，請參閱[資料來源和繫結 &#40;SSAS 多維度 &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 分析管理物件 (AMO) 物件模型中的對應元素是<xref:Microsoft.AnalysisServices.TimeBinding>。  
  
## <a name="see-also"></a>另請參閱  
 [Analysis Services 指令碼語言 XML 資料類型 &#40;ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
