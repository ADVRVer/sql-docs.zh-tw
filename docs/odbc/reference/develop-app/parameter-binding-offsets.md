---
title: 參數繫結位移 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- offsets of parameters [ODBC]
- binding offsets of parameters [ODBC]
ms.assetid: 309339e9-9ccd-4a58-8aa4-b6dc88f4eb7c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d0dbddc71b0d647246d10dad16ad72d533df16de
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68023355"
---
# <a name="parameter-binding-offsets"></a>參數繫結位移
應用程式可以指定的位移會新增至繫結參數緩衝區的位址和對應的長度/指標緩衝區位址何時**SQLExecDirect**或是**SQLExecute**呼叫。 這些新增內容的結果判斷這些作業中使用的位址。  
  
 繫結位移允許應用程式變更繫結，而不會呼叫**SQLBindParameter**之前繫結參數。 呼叫**SQLBindParameter**重新繫結參數變更緩衝區的位址和長度/指標的指標。 重新繫結使用的位移、 相反地，只要將位移加入現有的繫結的參數緩衝區位址和長度/指標緩衝區位址。 當使用位移時，繫結都是 「 範本 」 的應用程式緩衝區的配置方式和應用程式可以藉由變更位移到不同區域的記憶體中移動這個 「 範本 」。 新的位移可以指定在任何時間，而且永遠會加入到原始的繫結的值。  
  
 若要指定繫結位移，應用程式會將 SQL_ATTR_PARAM_BIND_OFFSET_PTR 陳述式屬性設定為 SQLINTEGER 緩衝區的位址。 應用程式會呼叫使用繫結的函式之前，就會將位移 （位元組），在此緩衝區中，只要參數緩衝區位址和長度/指標緩衝區位址都不是 0，且繫結的參數是 SQL 陳述式中。 位址和位移的總和必須是有效的位址。 （這表示，或兩個位移和加入位移的位址可以是無效，只要其總和會是有效的位址）。  
  
> [!NOTE]  
>  ODBC 2 不支援繫結位移。*x*驅動程式。
