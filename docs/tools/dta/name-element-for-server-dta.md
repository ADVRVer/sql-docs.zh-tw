---
title: 項目名稱伺服器 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: 4c94754d-6d62-4357-8ce7-f107ebf90c71
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7e88a41d433b4d3eaed9cc86a5a1a7696efaf69a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47799896"
---
# <a name="name-element-for-server-dta"></a>伺服器的 Name 元素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  包含您要微調的資料庫所在的伺服器名稱。  
  
## <a name="syntax"></a>語法  
  
```  
  
...code removed here...  
<Server>  
    <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|Description|  
|--------------------|-----------------|  
|**資料類型和長度**|**string**，在 1 和 255 個字元之間。|  
|**預設值**|無。|  
|**出現次數**|每個 **Server** 元素需要使用這個元素一次。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|--------------|  
|**父元素**|[Server 元素 &#40;DTA&#41;](../../tools/dta/server-element-dta.md)|  
|**子元素**|無。|  
  
## <a name="example"></a>範例  
 如需如何使用這個 **Name** 元素的範例，請參閱 [Server 元素 &#40;DTA&#41;](../../tools/dta/server-element-dta.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
