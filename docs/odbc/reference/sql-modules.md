---
title: SQL 模組 |Microsoft 文件
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
- SQL modules [ODBC]
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], modules
- modules [ODBC]
- SQL statements [ODBC], modules
ms.assetid: 07551472-87ee-4765-951f-1364ed32f0c0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10957c8e4a847f13d2dbf4b427382e65ea404c1f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915543"
---
# <a name="sql-modules"></a>SQL 模組
傳送至 DBMS 的 SQL 陳述式的第二個技巧是透過模組。 簡言之，模組包含群組的程序，它會呼叫從主應用程式的程式設計語言。 每個程序包含單一的 SQL 陳述式，且資料會傳遞與程序參數。  
  
 模組可以視為物件程式庫連結至應用程式程式碼。 不過，完全如何與應用程式的其餘部分的程序連結是視實作而定。 例如，無法編譯成目的碼與直接連結到應用程式程式碼的程序、 無法編譯並存放在 DBMS 和存取計劃識別碼放入應用程式程式碼的呼叫或它們無法在執行階段解譯。  
  
 模組的主要優點是它們完全分隔的程式設計語言的 SQL 陳述式。 理論上來說，它應該即可變更而不變更另一個只是將它們重新連結。
