---
title: MaxActiveConnections 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MaxActiveConnections Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- MaxActiveConnections element
ms.assetid: 0dc5b64d-061d-409f-95c0-4c63f87f5ee4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 32947054d4bdeaec091584f5c5921e2311a66f33
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090568"
---
# <a name="maxactiveconnections-element-assl"></a>MaxActiveConnections 元素 (ASSL)
  包含衍生自項目所允許的同時連線數目上限[DataSource](../data-type/datasource-data-type-assl.md)資料型別。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<DataSource>  
   ...  
   <MaxActiveConnections>...</MaxActiveConnections>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|Integer|  
|預設值|`10`|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[DataSource](../data-type/datasource-data-type-assl.md)|  
|子元素|None|  
  
## <a name="remarks"></a>備註  
 如果這個元素的值設定為零，最大並行連接數目就會由用來存取資料來源的資料夾決定。 如果這個元素的值設定為負值，最大並行連接數目就是無限制。  
  
## <a name="see-also"></a>另請參閱  
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  
