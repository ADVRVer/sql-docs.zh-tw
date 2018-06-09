---
title: Original 元素 (XMLA) |Microsoft 文件
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0ddf701f236e66680f562fa0721bcc8a2eb179f8
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575930"
---
# <a name="original-element-xmla"></a>Original 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  包含所使用的原始檔案系統儲存位置[資料夾](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Folder>  
   ...  
   <Original>...</Original>  
   ...  
</Folder>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|String|  
|預設值|無|  
|基數|1-1：只出現一次的必要元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[資料夾](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 **原始**元素包含 UNC 路徑的值以取代[新增](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md)包含父代的項目**資料夾**還原的所有物件的項目或已同步處理期間分別[還原](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)或[Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)命令。 這個項目的值進行比較的值[StorageLocation](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)每個 cube、 量值群組或資料分割的項目，如果找到符合的值便**新增**元素用來更新**StorageLocation**還原或同步處理期間的物件。  
  
 如需有關備份和還原物件的詳細資訊，請參閱[備份、 還原及同步處理資料庫&#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)。  
  
## <a name="see-also"></a>另請參閱
 [屬性&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
