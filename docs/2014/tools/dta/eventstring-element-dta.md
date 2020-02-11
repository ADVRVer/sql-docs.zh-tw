---
title: EventString 元素（DTA） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- EventString element
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 30e46515fda5bf03a96e9f1168b470f635698d07
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211110"
---
# <a name="eventstring-element-dta"></a>EventString 元素 (DTA)
  在 XML 輸入檔中，直接指定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼工作負載。  
  
## <a name="syntax"></a>語法  
  
```  
  
<Workload>  
    <EventString Weight="...">  
    ...code removed here...  
    </EventString>  
</Workload>  
```  
  
## <a name="element-attributes"></a>元素屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`Weight`|選擇性。 針對指定事件來指定查詢加權因數 (重要性因數)。 請利用 `float` 資料類型來指定加權。 例如，`Weight`="100.01"。 
  `Weight` 所能指定的最小值是 "0"。|  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|**資料類型和長度**|
  `string`，沒有長度限制。|  
|**預設值**|無。|  
|**出現次數**|如果未指定任何其他工作負載類型，便需要使用這個元素一次。 您必須指定 `EventString` 父系的 `File`、`Database` 或 `Workload` 子元素，但只能使用一種類型。 例如，如果您利用 `EventString` 元素指定了工作負載，便不能在相同 XML 輸入檔中，同時利用 `File` 元素來指定工作負載。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|--------------|  
|**父元素**|[&#40;DTA&#41;的工作負載元素](workload-element-dta.md)|  
|**子元素**|無。|  
  
## <a name="example"></a>範例  
 此元素的使用方式範例，請參閱 [XML Input File Sample with Inline Workload &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md) (內嵌工作負載的 XML 輸入檔範例 (DTA))。  
  
## <a name="see-also"></a>另請參閱  
 [XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
