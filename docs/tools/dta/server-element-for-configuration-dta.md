---
title: "伺服器組態的元素 (DTA) |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
caps.latest.revision: "13"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4df65dc3db8f8c23aa0fd012ee834020839d1ce9
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="server-element-for-configuration-dta"></a>組態的 Server 元素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]包含您想要 Database Engine Tuning Advisor 評估假設性組態伺服器的識別資訊 (所指定**組態**項目)。  
  
## <a name="syntax"></a>語法  
  
```  
  
<Configuration>  
    <Server>  
...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|**資料類型和長度**|無。|  
|**預設值**|無。|  
|**出現次數**|每個 **Configuration** 元素需要一次。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|--------------|  
|**父元素**|[Configuration 元素 &#40; Dta& &#41;](../../tools/dta/configuration-element-dta.md)|  
|**子元素**|[伺服器 &#40; Dta& &#41; 的 name 元素](../../tools/dta/name-element-for-server-dta.md)<br /><br /> [Database 元素組態 &#40; Dta& &#41;](../../tools/dta/database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a>備註  
 您只能為 **Configuration** 元素指定一個 **Server** 元素。 在 **Database Engine Tuning Advisor XML 結構描述** 中，這個元素的名稱為 [ServerTypecomplexType](http://go.microsoft.com/fwlink/?linkid=43100)。 請勿混淆這個 **Server** 元素和 **DTAInput** 元素的子元素。 如需詳細資訊，請參閱 [Server 元素 &#40;DTA&#41;](../../tools/dta/server-element-dta.md)。  
  
## <a name="example"></a>範例  
 如需使用範例，請參閱[含使用者指定組態的 XML 輸入檔範例 &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XML 輸入檔參考 &#40;Database Engine Tuning Advisor&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
