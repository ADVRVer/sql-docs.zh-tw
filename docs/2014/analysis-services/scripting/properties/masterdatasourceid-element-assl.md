---
title: MasterDatasourceID 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MasterDatasourceID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MasterDatasourceID
helpviewer_keywords:
- MasterDatasourceID element
ms.assetid: a9cbd3a9-581f-4a08-93d8-e1eea8757ce9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d967add587db8db34a8e6f07ce31bee8389f777e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201419"
---
# <a name="masterdatasourceid-element-assl"></a>MasterDatasourceID 元素 (ASSL)
  包含主要資料來源識別碼 (ID)[資料庫](../objects/database-element-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Database>  
   ...  
   <MasterDatasourceID>...</MasterDatasourceID>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|String|  
|預設值|None|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[[資料庫]](../objects/database-element-assl.md)|  
|子元素|None|  
  
## <a name="remarks"></a>備註  
 遠端執行個體上的資料庫[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]包含遠端資料分割`MasterDatasourceID`項目包含資料來源的資料來源的識別碼，用以識別的主要執行個體[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]管理遠端資料分割。  
  
 對應至父系的元素`MasterDatasourceID`在 「 分析管理物件 (AMO) 物件模型是<xref:Microsoft.AnalysisServices.Database>。  
  
## <a name="see-also"></a>另請參閱  
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  
