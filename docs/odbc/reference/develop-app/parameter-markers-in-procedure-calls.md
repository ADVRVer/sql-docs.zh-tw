---
title: 程序呼叫中的參數標記 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- parameter markers [ODBC]
- interoperability of SQL statements [ODBC], parameter markers
ms.assetid: cda56f2b-6eec-4cbc-8dbb-36d8fa9f9216
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00aa87461c1b4a82fbedc7bd7faf1da6ff327265
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199141"
---
# <a name="parameter-markers-in-procedure-calls"></a>程序呼叫中的參數標記
在呼叫接受參數的程序，可互通的應用程式應該使用參數標記，而不是常值的參數值。 某些資料來源不支援在程序呼叫中使用常值的參數值。 如需有關參數的詳細資訊，請參閱 <<c0> [ 陳述式參數](../../../odbc/reference/develop-app/statement-parameters.md)。 如需有關呼叫程序的詳細資訊，請參閱[程序呼叫](../../../odbc/reference/develop-app/procedure-calls.md)稍後這一節。
