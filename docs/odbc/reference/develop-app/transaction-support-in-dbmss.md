---
title: Dbms 中的交易支援 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 0fc2ae34-4748-4120-9fc3-bb28c8ed867e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2fed5ea04e15002d31e35e25fac405a729929be8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692266"
---
# <a name="transaction-support-in-dbmss"></a>DBMS 中的交易支援
某些資料庫中，例如 dBASE、 Paradox、 和 Btrieve，尤其是桌面資料庫不支援交易。 也支援交易的資料庫，在沒有變化的 SQL 陳述式的類型可以是在交易中。 如需詳細資訊，請參閱中的 SQL_TXN_CAPABLE 選項[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)函式描述。
