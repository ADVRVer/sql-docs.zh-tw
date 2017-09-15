---
title: "要逸出序列 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC escape sequences [ODBC], LIKE
- LIKE escape sequence [ODBC]
- escape sequences [ODBC], LIKE
ms.assetid: 798d75ea-be9d-4bef-b297-318bc327f1ca
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 678f2f8f720823ef5658ba7ee1e1391bbebc1c50
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="like-escape-sequence"></a>要逸出序列
ODBC 會逸出序列使用 LIKE 子句。 此逸出序列語法如下所示：  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>備註  
 在 BNF 標記法，語法如下所示：  
  
 *ODBC 類似-逸出*:: =  
  
 *起始 esc ODBC 端*逸出 '*逸出字元*' *ODBC esc 結束字元*  
  
 *逸出字元*:: =*字元*  
  
 *起始 esc ODBC 端*:: = {  
  
 *ODBC esc 結束字元*:: =}  
  
 若要判斷驅動程式是否支援 LIKE 逸出序列，應用程式可以呼叫**SQLGetInfo** SQL_LIKE_ESCAPE_CLAUSE 資訊類型。
