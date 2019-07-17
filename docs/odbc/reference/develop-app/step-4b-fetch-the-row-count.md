---
title: 步驟 4b：擷取的資料列計數 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- fetches [ODBC], fetching row count
- row count [ODBC]
- application process [ODBC], fetching row count
ms.assetid: 3af481b1-d694-446e-948d-e3a5edcad050
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9455c6589ed93a51e404f3e50d1cb86a0c0c8476
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114163"
---
# <a name="step-4b-fetch-the-row-count"></a>步驟 4b：擷取資料列計數
下一步是擷取資料列計數，如下圖所示。  
  
 ![顯示提取資料列計數](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 如果在步驟 3 中執行的陳述式已**更新**，**刪除**，或**插入**陳述式中，應用程式會擷取與受影響的資料列計數**SQLRowCount**。 如需詳細資訊，請參閱 <<c0> [ 判斷受影響的資料列數目](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)。  
  
 應用程式現在會回到步驟 3 相同交易中執行另一個陳述式，或繼續進行步驟 5 以認可或回復交易。
