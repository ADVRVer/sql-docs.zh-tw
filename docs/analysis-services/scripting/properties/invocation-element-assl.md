---
title: Invocation 元素 (ASSL) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Invocation Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Invocation
helpviewer_keywords:
- Invocation element
ms.assetid: f6bf64ad-ae57-4d46-bf92-1d07a65378bb
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 78326ec2c6e68dff1bc77d18c99a643c43a33239
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="invocation-element-assl"></a>Invocation 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  指定如何[動作](../../../analysis-services/scripting/objects/action-element-assl.md)應叫用。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Action>  
   ...  
   <Invocation>...</Invocation>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|字串 (列舉)|  
|預設值|*互動式*|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[動作](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 動作的引動過程取決於用戶端應用程式。 **引動過程**用戶端應用程式如何動作應處理，並不表示執行個體建議的項目[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]如何叫用動作。  
  
 這個元素的值限制為下表所列的其中一個字串。  
  
|Value|Description|  
|-----------|-----------------|  
|*互動式*|由使用者以互動方式叫用。|  
|*省略符號*|當用戶端應用程式開啟物件時叫用。|  
|*批次*|由批次處理命令叫用。|  
  
 列舉型別對應至允許的值**引動過程**在 「 分析管理物件 (AMO) 物件模型而言， <xref:Microsoft.AnalysisServices.Action>。  
  
## <a name="see-also"></a>另請參閱  
 [屬性 & #40;ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
