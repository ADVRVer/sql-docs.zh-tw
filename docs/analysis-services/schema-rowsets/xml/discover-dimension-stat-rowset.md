---
title: "DISCOVER_DIMENSION_STAT 資料列集 |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 639f8cd7-3b43-40d5-8b84-552daf60d484
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7fb30b200d930a9827aee4b630d80df6e622842e
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2018
---
# <a name="discoverdimensionstat-rowset"></a>DISCOVER_DIMENSION_STAT 資料列集
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
提供維度的相關資訊，包括包含維度之資料庫的名稱、維度名稱、其屬性，以及每個屬性之成員的計數。 在表格式模型中，這會對應至資料表中的資料行，以及每個資料行中值的數目。  
  
 **適用於：**表格式模型、 多維度模型  
  
## <a name="rowset-columns"></a>資料列集資料行  
 **DISCOVER_DIMENSION_STAT**資料列集包含下列資料行。  
  
|資料行名稱|類型指標|限制|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|必要項|包含維度的資料庫名稱。<br /><br /> 這個資料行是限制清單中的必要項。|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**|必要項|維度的名稱。<br /><br /> 這個資料行是限制清單中的必要項。|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**||維度中屬性的名稱。|  
|**ATTRIBUTE_COUNT**|**DBTYPE_I8**||具名屬性中值的計數。 在表格式模型中，此值一定與資料表中的資料列數目相同。|  
  
 這個結構描述資料列集並未排序。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>使用 ADOMD.NET 傳回資料列集  
 使用 ADOMD.NET 和結構描述資料列集來擷取中繼資料時，您可以使用 GUID 或字串，在 GetSchemaDataSet 方法中參考結構描述資料列集物件。 如需詳細資訊，請參閱 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)。  
  
 下表將提供可識別此資料列集的 GUID 和字串值。  
  
|引數|值|  
|--------------|-----------|  
|GUID|a07ccd90-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionDimensionStat|  
  
## <a name="see-also"></a>另請參閱  
 [XML for Analysis 結構描述資料列集](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
