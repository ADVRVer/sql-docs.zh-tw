---
title: CompareEnum |Microsoft 文件
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CompareEnum
helpviewer_keywords:
- CompareEnum enumeration [ADO]
ms.assetid: bc8f710d-0621-4673-8d8e-0361e44abed0
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db29f164e3329044f0d4ed12d2353e206bb87172
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="compareenum"></a>CompareEnum
指定兩筆記錄，其書籤所代表的相對位置。  
  
|常數|Value|Description|  
|--------------|-----------|-----------------|  
|**adCompareEqual**|1|指出書籤相等。|  
|**adCompareGreaterThan**|2|指出第一個書籤之後，第二個。|  
|**adCompareLessThan**|0|表示第一個書籤前，第二個。|  
|**adCompareNotComparable**|4|表示書籤無法進行比較。|  
|**adCompareNotEqual**|3|指出書籤不相等和不排序。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 封裝： **com.ms.wfc.data**  
  
|常數|  
|--------------|  
|AdoEnums.Compare.EQUAL|  
|AdoEnums.Compare.GREATERTHAN|  
|AdoEnums.Compare.LESSTHAN|  
|AdoEnums.Compare.NOTCOMPARABLE|  
|AdoEnums.Compare.NOTEQUAL|  
  
## <a name="applies-to"></a>適用於  
 [CompareBookmarks 方法 (ADO)](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [CompareBookmarks 方法 (ADO)](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)
