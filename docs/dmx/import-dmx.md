---
title: 匯入 (DMX) |Microsoft 文件
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- IMPORT
dev_langs:
- DMX
helpviewer_keywords:
- IMPORT statement
- mining structures [DMX], importing
ms.assetid: c053bc88-2daf-4ebb-81d7-5a330250536d
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 162bc8fc7497d3e8b425e09b81c13a24adb75678
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="import-dmx"></a>IMPORT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  從 Analysis Services 備份檔案 (.abf) 中將採礦模型或採礦結構載入到伺服器。  
  
## <a name="syntax"></a>語法  
  
```  
  
IMPORT FROM <filename>  
```  
  
## <a name="arguments"></a>引數  
 *filename*  
 包含要匯入檔案之名稱與位置的字串。  
  
## <a name="remarks"></a>備註  
 如果未指定物件，則會載入 .dmb 檔案的全部內容。 如果 .dmb 檔案包含的資料庫不存在伺服器上，則會建立資料庫。  
  
 您必須是資料庫或伺服器管理員，才能匯出或匯入物件。  
  
## <a name="import-from-file-example"></a>從檔案匯入的範例  
 下列範例會將包含關聯模型和結構之檔案的完整內容匯入目前的伺服器。  
  
```  
IMPORT FROM 'C:\TEMP\Association_NEW.dmb'  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦延伸模組&#40;DMX&#41;資料定義陳述式](../dmx/dmx-statements-data-definition.md)   
 [資料採礦延伸模組&#40;DMX&#41;資料操作陳述式](../dmx/dmx-statements-data-manipulation.md)   
 [資料採礦延伸模組 & #40; DMX & #41;陳述式參考](../dmx/data-mining-extensions-dmx-statements.md)   
 [匯出&AMP;#40;DMX&AMP;#41;](../dmx/export-dmx.md)   
 [匯出和匯入資料採礦物件](../analysis-services/data-mining/export-and-import-data-mining-objects.md)  
  
  
