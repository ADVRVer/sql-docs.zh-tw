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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2feab58de28e39747a1d9c819f9f15426b156151
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306271"
---
# <a name="calling-sqlclosecursor"></a>呼叫 SQLCloseCursor
由於**SQLCloseCursor**與使用 SQL_CLOSE 的**SQLFreeStmt**幾乎相同，因此驅動程式管理員不會對應此函式。 取代函式會對應，如此*一來，現有的 odbc* *2.x 應用程式*就可以使用新的函式輕鬆地移至 ODBC 3.x。 這種移動可讓這類應用程式以模組化的方式，更輕鬆地開始在條件式程式碼內使用新*的 ODBC 3.x 功能。* **SQLCloseCursor**不代表任何新功能。 藉由使用 SQL_CLOSE 從**SQLFreeStmt**移至**SQLCloseCursor** ，應用程式無法獲得任何好處。
