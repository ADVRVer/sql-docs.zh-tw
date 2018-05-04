---
title: 在 CREATE TABLE 陳述式中非 NULL |Microsoft 文件
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
- not null [ODBC]
- interoperability [ODBC], not null
ms.assetid: 3fb69943-f0c9-4ed2-aa42-20440e37e49d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 63e2ed384033370b91a8321ad9c6165b72570f72
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="not-null-in-create-table-statements"></a>未在 CREATE TABLE 陳述式中的 NULL
不支援某些資料庫，並特別桌面資料庫， **NOT NULL**中的資料行條件約束**CREATE TABLE**陳述式。 如需詳細資訊，請參閱中的 SQL_NON_NULLABLE_COLUMNS 選項[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)函式描述。
