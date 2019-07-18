---
title: LIKE 逸出序列 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC escape sequences [ODBC], LIKE
- LIKE escape sequence [ODBC]
- escape sequences [ODBC], LIKE
ms.assetid: 798d75ea-be9d-4bef-b297-318bc327f1ca
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 629ceaf666ae732d0838a216272c308dcb5b5658
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041708"
---
# <a name="like-escape-sequence"></a>LIKE 逸出序列
ODBC 會將逸出序列用於 LIKE 子句。 此逸出序列的語法如下所示：  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>備註  
 在 backus-naur form，BNF 標記法中，語法如下所示：  
  
 *ODBC-like-escape* ::=  
  
 *ODBC-esc-啟動器*逸出 '*逸出字元*' *ODBC esc 鍵結束字元*  
  
 *escape-character* ::= *character*  
  
 *起始 esc ODBC 端*:: = {  
  
 *ODBC esc 鍵結束字元*:: =}  
  
 若要判斷驅動程式是否支援 LIKE 逸出序列，應用程式可以呼叫**SQLGetInfo** SQL_LIKE_ESCAPE_CLAUSE 資訊類型。
