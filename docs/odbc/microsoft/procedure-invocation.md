---
title: 程序引動過程 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], procedure invocation
- procedure invocation [ODBC]
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bc37ef6d268dba71f8270909ea9c5b938ef3ee75
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070488"
---
# <a name="procedure-invocation"></a>程序引動過程
使用 Microsoft Access 驅動程式時，程序可以使用叫用從驅動程式**SQLExecDirect**或是**SQLPrepare**函式，使用下列語法: {呼叫*程序名稱* [(*參數*[，*參數*]...)]}。 請注意，運算式不支援做為參數，呼叫的程序。  
  
 如果是程序名稱包含以連字號，名稱必須加以分隔後括住 （'）。  
  
 可以使用前一個陳述式來呼叫參數化的查詢。
