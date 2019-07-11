---
title: 呼叫 SQLCloseCursor |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], SQLCloseCursor
- backward compatibility [ODBC], SqlCloseCursor
- SQLCloseCursor function [ODBC], calling
- upgrading applications [ODBC], SQLCloseCursor
- compatibility [ODBC], SQLCloseCursor
ms.assetid: ef448c39-a9ad-4f07-8ef3-65bd4cef672a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da5a674f86228c71a26e621936dc711a688a684d
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793936"
---
# <a name="calling-sqlclosecursor"></a>呼叫 SQLCloseCursor
因為**SQLCloseCursor**幾乎相同**SQLFreeStmt** SQL_CLOSE，與驅動程式管理員不會對應此函式。 取代函式對應，讓現有的 ODBC *2.x*應用程式可以輕鬆地移動到 ODBC *3.x*使用新的函式。 這類移動更容易之類的應用程式，若要開始使用新的 ODBC *3.x*模組化方式的條件式程式碼內的功能。 **SQLCloseCursor**不代表任何新功能。 移至應用程式不會得到任何優勢**SQLCloseCursor**從**SQLFreeStmt**與 SQL_CLOSE。
