---
title: "MasterDatasourceID 元素 (ASSL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MasterDatasourceID Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: MasterDatasourceID
helpviewer_keywords: MasterDatasourceID element
ms.assetid: a9cbd3a9-581f-4a08-93d8-e1eea8757ce9
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a883026e0fe728fb80f1c970b6bda95117a3b767
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="masterdatasourceid-element-assl"></a>MasterDatasourceID 元素 (ASSL)
  包含主要資料來源識別碼 (ID)[資料庫](../../../analysis-services/scripting/objects/database-element-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Database>  
   ...  
   <MasterDatasourceID>...</MasterDatasourceID>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|字串|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[資料庫](../../../analysis-services/scripting/objects/database-element-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 遠端執行個體上資料庫[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ，包含遠端資料分割， **MasterDatasourceID**項目包含用來識別主要資料來源識別碼的資料來源執行個體[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]管理遠端資料分割。  
  
 對應目的父代的項目**MasterDatasourceID**在 「 分析管理物件 (AMO) 物件模型而言， <xref:Microsoft.AnalysisServices.Database>。  
  
## <a name="see-also"></a>請參閱＜  
 [屬性 &#40;ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
