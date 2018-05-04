---
title: 診斷記錄 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- handles [ODBC], diagnostic records
- header records [ODBC]
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 92c73f9b-3ed7-410d-9cec-2771004aae60
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ba25e3f2c67146cb845f26abcef09b7fc956ae4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="diagnostic-records"></a>診斷記錄
與每個環境產生關聯，連接、 陳述式和描述項控制代碼會*診斷記錄*。 這些記錄會包含最後一個呼叫的函式，使用特定的控制代碼的診斷資訊。 另一個函式呼叫使用該控制代碼時，會取代記錄。 可以一次儲存的診斷記錄的數目沒有限制。  
  
 有兩種類型的診斷記錄：*標頭記錄*和零個或多個*狀態記錄*。 標頭記錄為記錄 0;狀態記錄會記錄 1 和更新版本。 診斷記錄所組成的個別欄位，不同標頭記錄和狀態記錄的數目。 此外，ODBC 元件也可以定義自己的診斷記錄欄位。  
  
 雖然診斷記錄可以視為結構，但沒有實際加以結構; 的需求驅動程式如何儲存診斷資訊是特定驅動程式。  
  
 在 診斷記錄的欄位會擷取與**SQLGetDiagField**。 SQLSTATE、 自發性錯誤號碼和狀態記錄的診斷訊息欄位可以使用的單一呼叫中擷取**SQLGetDiagRec**。  
  
 此章節包含下列主題。  
  
-   [標頭記錄](../../../odbc/reference/develop-app/header-record.md)  
  
-   [狀態記錄](../../../odbc/reference/develop-app/status-records.md)
