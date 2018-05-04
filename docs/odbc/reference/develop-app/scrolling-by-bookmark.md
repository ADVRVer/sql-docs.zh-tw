---
title: 書籤捲動 |Microsoft 文件
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
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
- scrolling rows [ODBC]
ms.assetid: 4862f098-41a4-4bd2-894e-f71bb97f9bc0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 823929a98b3fc7b016f8bc1dc3fa1c2ed982b9c0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="scrolling-by-bookmark"></a>捲動書籤
在提取資料列時， **SQLFetchScroll**，應用程式可以使用為基礎的書籤選取起始資料列。 這是一個絕對位址的形式，因為它不相依於目前的資料指標位置。 若要捲動到加上書籤的資料列，應用程式會呼叫**SQLFetchScroll**與*Sqlfetchscroll*要使用 sql_fetch_bookmark。 此作業使用 SQL_ATTR_FETCH_BOOKMARK_PTR 陳述式屬性所指向的書籤。 它會傳回資料列集，從該書籤識別的資料列開始。 應用程式可以指定這項作業中的位移*FetchOffset*引數呼叫**SQLFetchScroll**。 當指定的位移時，傳回的資料列集的第一個資料列由加入中的之數字*FetchOffset*書籤所識別之資料列數目的引數。 這種使用*FetchOffset* ODBC 2 搭配使用時，不支援引數。*x*驅動程式，則當應用程式呼叫**SQLFetchScroll** ODBC 2。*x*驅動程式搭配*Sqlfetchscroll*設定為要使用 SQL_FETCH_BOOKMARK， *FetchOffset*引數必須設定為 0。
