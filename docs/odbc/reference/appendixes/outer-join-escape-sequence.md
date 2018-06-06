---
title: 外部聯結逸出序列 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: af6a98b3e1a7848fa242dfceb890c472e1d16f74
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="outer-join-escape-sequence"></a>外部聯結逸出序列
ODBC 使用的外部聯結的逸出序列。 此逸出序列語法如下所示：  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>備註  
 在 BNF 標記法，語法如下所示：  
  
 *ODBC 外部-聯結的逸出*:: =  
  
 *起始 esc ODBC 端*oj*外部聯結 ODBC esc 結束字元*  
  
 *外部聯結*:: =*資料表名稱*[*相互關聯名稱*] {左&#124;右邊&#124;完整}  
  
 外部聯結 {*資料表名稱*[*相互關聯名稱*] &#124; *外部聯結*} ON  
  
 *搜尋-*  
  
 *條件*  
  
 *相互關聯名稱*:: =*使用者定義名稱*  
  
 *起始 esc ODBC 端*:: = {  
  
 *ODBC esc 結束字元*:: =}  
  
 若要判斷支援此陳述式的哪個部分，應用程式呼叫**SQLGetInfo** SQL_OJ_CAPABILITIES 資訊類型。 若為外部聯結，*搜尋條件*必須包含只之間指定聯結條件*資料表名稱*。
