---
title: 擷取中的描述項欄位的值 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 37efd70ccd8fa0ad5c6d4bb573eb1c158a3ec35b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>擷取中的描述項欄位的值
應用程式可以呼叫**SQLGetDescField**取得的單一欄位的描述項記錄。 **SQLGetDescField**在 ODBC 中定義的所有描述項欄位和驅動程式定義的欄位也會提供應用程式存取。  
  
 **SQLGetDescRec**可以呼叫以擷取多個會影響資料類型的描述項欄位的設定和儲存的資料行或參數的資料。
