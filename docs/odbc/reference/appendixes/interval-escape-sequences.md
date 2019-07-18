---
title: 間隔逸出序列 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interval literals [ODBC]
- escape sequences [ODBC], interval
- ODBC escape sequences [ODBC], interval
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 69c674ee8838273af9bf4ed91ddcead7e1768fb9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041646"
---
# <a name="interval-escape-sequences"></a>間隔逸出序列
ODBC 會將逸出序列用於間隔常值。 此逸出序列的語法如下所示：  
  
 {*interval-literal*}  
  
 Backus-naur form，BNF 語法*間隔 string-literal*，請參閱[間隔常值語法](../../../odbc/reference/appendixes/interval-literal-syntax.md)稍後本附錄一節。  
  
 如果資料來源所支援間隔資料類型，支援的間隔常值的逸出序列。 應用程式應該呼叫**SQLGetTypeInfo**來判斷是否支援這些資料類型。
