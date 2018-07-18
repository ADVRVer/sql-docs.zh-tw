---
title: Password 元素 (ASSL) |Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: cc5464e4530e00a0d12807cb0cef2c2e1aa22afa
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050666"
---
# <a name="password-element-assl"></a>Password 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  包含的使用者帳戶的密碼[ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<ImpersonationInfo  
   ...  
  <Password>...</Password>  
   ...  
</ImpersonationInfo>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|String|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 值**密碼**項目，以及值[帳戶](../../../analysis-services/scripting/properties/account-element-impersonationinfo-assl.md)項目，用於模擬用途，如果值[ImpersonationMode](../../../analysis-services/scripting/properties/impersonationmode-element-assl.md)項目任何項目衍生自**ImpersonationInfo**資料類型設為*ImpersonateAccount*。  
  
 只有伺服器管理員角色的成員[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]執行個體可以提供空白的值，如**密碼**項目  
  
## <a name="see-also"></a>另請參閱  
 [DataSourceImpersonationInfo 元素&#40;ASSL&#41;](../../../analysis-services/scripting/properties/datasourceimpersonationinfo-element-assl.md)   
 [屬性&#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
