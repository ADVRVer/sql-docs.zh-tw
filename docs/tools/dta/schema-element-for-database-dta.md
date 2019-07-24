---
title: 資料庫的 Schema 元素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Schema element
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d41a77ace5608acd649bc91f420fe65c9eb7a563
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68034560"
---
# <a name="schema-element-for-database-dta"></a>資料庫的 Schema 元素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  指定您要微調之資料庫的結構描述。  
  
## <a name="syntax"></a>語法  
  
```  
  
<Database>  
...code removed here...  
    <Schema>...</Schema>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|Description|  
|--------------------|-----------------|  
|**資料類型和長度**|無。|  
|**預設值**|無。|  
|**出現次數**|**Server** 元素之下所指定的 **Database** 元素需要使用這個元素一次。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|--------------|  
|**父元素**|[伺服器的 Database 元素 &#40;DTA&#41;](../../tools/dta/database-element-for-server-dta.md)|  
|**子元素**|[結構描述的 Name 元素 &#40;DTA&#41;](../../tools/dta/name-element-for-schema-dta.md)<br /><br /> [結構描述的 Table 元素 &#40;DTA&#41;](../../tools/dta/table-element-for-schema-dta.md)|  
  
## <a name="example"></a>範例  
 如需此元素的使用範例，請參閱 [Server 元素 &#40;DTA&#41;](../../tools/dta/server-element-dta.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
