---
title: 識別項大小寫 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6445cffd5faa8b825c81ec729d7b28c90e14a7b3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678348"
---
# <a name="identifier-case"></a>識別碼大小寫
在 SQL 陳述式和類別目錄函式引數，識別項和引號識別項可以是區分大小寫或不是，應用程式可以呼叫來判斷**SQLGetInfo** SQL_QUOTED_ SQL_IDENTIFIER_CASE 與IDENTIFIER_CASE 選項。  
  
 每個選項有四個可能的傳回值： 一個指出的識別碼或引號識別項的情況下會區分大小和三個指出不敏感。 三個值不區分大小寫的進一步描述儲存在系統目錄的識別碼的情況。 在系統目錄來儲存識別碼是關於僅用於顯示用途，例如當應用程式會顯示目錄函數; 的結果它不會變更識別碼的區分大小寫。
