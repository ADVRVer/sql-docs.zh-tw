---
title: PropertyAttributesEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PropertyAttributesEnum
helpviewer_keywords:
- PropertyAttributesEnum enumeration [ADO]
ms.assetid: 96a01955-a6b4-4cbf-9c73-52bcd1e9fb25
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 99acfb2507701f0e4b47aff5b0595b61fc45c425
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719143"
---
# <a name="propertyattributesenum"></a>PropertyAttributesEnum
指定的屬性[屬性](../../../ado/reference/ado-api/property-object-ado.md)物件。  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|**adPropNotSupported**|0|指出提供者不支援的屬性。|  
|**adPropRequired**|1|表示使用者在初始化資料來源之前，必須指定此屬性的值。|  
|**adPropOptional**|2|表示使用者不需要初始化資料來源之前指定這個屬性的值。|  
|**adPropRead**|512|表示使用者可以讀取的屬性。|  
|**adPropWrite**|1024|表示使用者可以設定屬性。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 封裝： **com.ms.wfc.data**  
  
|常數|  
|--------------|  
|AdoEnums.PropertyAttributes.NOTSUPPORTED|  
|AdoEnums.PropertyAttributes.REQUIRED|  
|AdoEnums.PropertyAttributes.OPTIONAL|  
|AdoEnums.PropertyAttributes.READ|  
|AdoEnums.PropertyAttributes.WRITE|  
  
## <a name="applies-to"></a>適用於  
 [Attributes 屬性 (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
