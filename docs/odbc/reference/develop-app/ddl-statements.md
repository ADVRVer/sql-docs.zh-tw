---
title: DDL 陳述式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], DDL statements
- DDL statements [ODBC]
ms.assetid: 96ac9859-5976-4b06-ae1f-2fec3231e266
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97541c9d594b282b871cb7869d0e8c2d2224205d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68076858"
---
# <a name="ddl-statements"></a>DDL 陳述式
資料定義語言 (DDL) 陳述式而異 Dbms 極大的差異。 ODBC SQL 定義陳述式中的最常見的資料定義作業： 建立和卸除資料表、 索引和檢視;改變資料表;授與和撤銷的權限。 所有其他 DDL 陳述式是資料來源特有。 因此，互通的應用程式無法執行某些資料定義作業。 一般情況下，這並不是問題，因為這類作業傾向於較高的 DBMS 特定和最左邊的專屬資料庫管理軟體隨附於大部分的 Dbms，或安裝程式隨附的驅動程式。  
  
 在資料定義中的另一個問題是該名稱可大幅不同 Dbms 之間的資料型別。 而不是定義標準的資料型別名稱，並強制驅動程式，以將它們轉換成特定 DBMS 的名稱， **SQLGetTypeInfo**可讓應用程式探索特定 DBMS 的資料型別名稱。 互通的應用程式應該使用 SQL 陳述式中這些名稱來建立和變更資料表。所列的名稱[附錄 c:SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)，和[附錄 d:資料型別](../../../odbc/reference/appendixes/appendix-d-data-types.md)，只是範例。
