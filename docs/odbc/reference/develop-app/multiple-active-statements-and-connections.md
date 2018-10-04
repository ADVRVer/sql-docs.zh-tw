---
title: 多個作用中陳述式和連線 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], multiple active statements and connections
- multiple active statements and connections [ODBC]
ms.assetid: a6571356-b23e-4f10-a17b-bce09460b71e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b2a1edbf9947aff01ef6d4688959352986cf672d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745716"
---
# <a name="multiple-active-statements-and-connections"></a>多個作用中陳述式和連線
有些驅動程式和 Dbms 的陳述式和可同時處於作用中的連接數目的限制。 這些數字可以很小，做為其中一個。 如需詳細資訊，請參閱 「 SQL_MAX_CONCURRENT_ACTIVITIES 和 SQL_MAX_DRIVER_CONNECTIONS 選項[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)函式的描述，以及[陳述式會處理](../../../odbc/reference/develop-app/statement-handles.md)和[連接控制代碼](../../../odbc/reference/develop-app/connection-handles.md)。
