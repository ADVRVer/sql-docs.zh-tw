---
title: 程序引動過程 |Microsoft 文件
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
- SQL grammar [ODBC], procedure invocation
- procedure invocation [ODBC]
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6eb0abafb72b0acd9424a31205771c91edbc5529
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="procedure-invocation"></a>程序引動過程
使用 Microsoft Access 驅動程式時，程序可以叫用從驅動程式使用**SQLExecDirect**或**SQLPrepare**函式搭配下列語法: {呼叫*程序名稱* [(*參數*[，*參數*]...)]}。 請注意，做為參數，呼叫的程序不支援運算式。  
  
 如果程序名稱包含破折號，必須為反引號 （'） 分隔名稱。  
  
 參數化的查詢，可以使用前一個陳述式來呼叫。
