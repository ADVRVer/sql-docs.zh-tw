---
title: "Server 元素 (DTA) |Microsoft 文件"
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
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
caps.latest.revision: "16"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 32f1958fcf5b69d9a3b8ef7b3fdf63f67216d9d0
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="server-element-dta"></a>Server 元素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]包含資料庫所在您要微調伺服器的識別資訊。  
  
## <a name="syntax"></a>語法  
  
```  
  
<DTAInput>  
    <Server>  
    ...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|**資料類型和長度**|無。|  
|**預設值**|無。|  
|**出現次數**|每個 **DTAInput** 元素都需要使用這個元素一次。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|--------------|  
|**父元素**|[DTAInput 元素 &#40; Dta& &#41;](../../tools/dta/dtainput-element-dta.md)|  
|**子元素**|[伺服器 &#40; Dta& &#41; 的 name 元素](../../tools/dta/name-element-for-server-dta.md)<br /><br /> [Database 元素的伺服器 &#40; Dta& &#41;](../../tools/dta/database-element-for-server-dta.md)|  
  
## <a name="remarks"></a>備註  
 您只能為 **DTAInput** 元素指定一個 **Server** 元素。 在 DTA XML 結構描述中，這個元素是 **ServerDetailsTypecomplexType** 名稱。 請勿混淆這個 **Server** 元素和 **Configuration** 元素的子元素。 如需詳細資訊，請參閱[組態的 Server 元素 &#40;DTA&#41;](../../tools/dta/server-element-for-configuration-dta.md)。  
  
## <a name="example"></a>範例  
 下列範例顯示如何在 SERVER001 的 **AdventureWorks** 資料庫中，指定 **Sales.SalesPerson** 資料表：  
  
```xml  
<Server>  
  <Name>SERVER001</Name>  
  <Database>  
    <Name>AdventureWorks</Name>  
    <Schema>  
      <Name>Sales</Name>  
      <Table>  
        <Name>SalesPerson</Name>  
      </Table>  
    </Schema>  
  </Database>  
</Server  
```  
  
## <a name="see-also"></a>另請參閱  
 [XML 輸入檔參考 &#40;Database Engine Tuning Advisor&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
