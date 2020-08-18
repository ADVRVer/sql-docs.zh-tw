---
description: DELETE (DMX)
title: 刪除 (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c6050a387af893e984b95c036181b7f16a269dc0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491532"
---
# <a name="delete-dmx"></a>DELETE (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  根據您使用的資料採礦延伸模組 (DMX) 子句，清除採礦模型、採礦結構，或採礦結構及其所有相關聯的採礦模型。  
  
## <a name="syntax"></a>語法  
  
```  
  
DELETE FROM [MINING MODEL] <model>[.CONTENT]  
DELETE FROM [MINING STRUCTURE] <structure>[.CONTENT]|[.CASES]  
```  
  
## <a name="arguments"></a>引數  
 *model*  
 模型識別碼。  
  
 *結構*  
 結構識別碼。  
  
## <a name="remarks"></a>備註  
 如果您沒有指定 [ **採礦模型** ] 或 [ **採礦結構**]，則會 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 根據名稱搜尋物件類型，並處理正確的物件。 如果伺服器包含具有相同名稱的採礦結構與採礦模型，就會傳回錯誤。  
  
 下表說明使用不同語法格式的結果。  
  
|引數|結果|  
|---------------|------------|  
|從採礦結構刪除*\<structure>*<br /><br /> 或<br /><br /> 從採礦結構刪除 *\<structure>* 。內容|在採礦結構上執行 ProcessClear。 清除採礦結構及其相關聯的採礦模型中所有的內容。|  
|從採礦結構刪除 *\<structure>* 。例|在採礦結構上執行 ProcessClearStructureOnly。 清除採礦結構中所有的內容，但是相關聯的採礦模型則保持不變。 清除採礦結構之後，在相關聯之採礦模型上的鑽研將會失敗。|  
|從採礦模型刪除*\<model>*<br /><br /> 或<br /><br /> 從採礦模型刪除 *\<model>* 。內容|在模型上執行 ProcessClear，但不會讓狀態值保持不變。 狀態值是資料行的可能狀態。 例如，性別資料行的狀態值為男性與女性。|  
  
 如需處理類型的詳細資訊，請參閱 [Type Element &#40;XMLA&#41;](https://docs.microsoft.com/analysis-services/xmla/xml-elements-properties/type-element-xmla)。  
  
## <a name="examples"></a>範例  
 下列範例會移除 NB_Sample 模型中的所有內容。  
  
```  
DELETE FROM NB_Sample.CONTENT  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦延伸模組 &#40;DMX&#41; 資料定義語句](../dmx/dmx-statements-data-definition.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 資料動作陳述式](../dmx/dmx-statements-data-manipulation.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 陳述式參考](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
