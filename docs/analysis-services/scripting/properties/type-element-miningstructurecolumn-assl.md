---
title: "輸入元素 (MiningStructureColumn) (ASSL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Type Element (MiningStructureColumn)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: TYPE
helpviewer_keywords: Type element
ms.assetid: ce999716-9487-4348-bc42-270a2026a452
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 15c18862d04cd5e50bd80238fcb3d649a3d835cd
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2017
---
# <a name="type-element-miningstructurecolumn-assl"></a>Type 元素 (MiningStructureColumn) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]包含的型別[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<MiningStructureColumn>  
   ...  
   <Type>...</Type>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|字串 (列舉)|  
|預設值|無|  
|基數|1-1：只出現一次的必要元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 這個元素的值限制為下表所列的其中一個字串。  
  
|值|Description|  
|-----------|-----------------|  
|*長*|64 位元帶正負號的整數。 此資料類型會對應至**Int64**中的資料類型[!INCLUDE[msCoName](../../../includes/msconame-md.md)]OLE DB 中的.NET Framework 和的 DBTYPE_I8 資料類型。|  
|*布林*|布林值。 此資料類型會對應至**布林**.NET Framework 和 OLE DB 中的 DBTYPE_BOOL 資料類型中的資料型別。|  
|*Text*|Unicode 字元的以 Null 結束資料流。 此資料類型會對應至**字串**.NET Framework 和 OLE DB 中的 DBTYPE_WSTR 資料類型中的資料型別。|  
|*Double*|在 -1.79E +308 到 1.79E +308 範圍中的雙精確度浮點數。 此資料類型會對應至**Double** .NET Framework 和 OLE DB 中的 DBTYPE_R8 資料類型中的資料型別。|  
|*日期*|儲存成雙精確度浮點數的日期資料。 整數部分為自 1899 年 12 月 30 日起的天數，而分數部分則為一天的分數部分。 此資料類型會對應至**DateTime** .NET Framework 和 OLE DB 中的 DBTYPE_DATE 資料類型中的資料型別。|  
|*Table*|巢狀資料表。 這個資料類型會對應至 OLE DB 中的 DBTYPE_HCHAPTER 資料類型。<br /><br /> 注意： 在.NET Framework 中的資料表資料行沒有對等的內建資料型別，但是改為支援**DataReader**類別。|  
  
 列舉型別對應至允許的值**類型**在 「 分析管理物件 (AMO) 物件模型而言， <xref:Microsoft.AnalysisServices.MiningStructureColumnTypes>。  
  
 對應目的父代的項目**類型**在 「 分析管理物件 (AMO) 物件模型而言， <xref:Microsoft.AnalysisServices.MiningStructureColumn>。  
  
## <a name="see-also"></a>請參閱  
 [屬性 &#40;ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
