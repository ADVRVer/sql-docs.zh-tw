---
title: SQL_ARD_TYPE |Microsoft 文件
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
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], SQL_ARD_TYPE
- SQL_ARD_TYPE [ODBC]
ms.assetid: 8d87ca10-f955-4284-8689-e9f4cc31e7ae
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4e3d3ba38947babc5e7335fd38a63db18943b31f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907143"
---
# <a name="sqlardtype"></a>SQL_ARD_TYPE
SQL_ARD_TYPE 類型識別碼用來表示緩衝區中的資料將會於 ARD SQL_DESC_CONCISE_TYPE 欄位中指定的型別。 SQL_ARD_TYPE 進入*TargetType*引數呼叫**SQLGetData**而不是特定資料類型，而且可讓您變更資料的應用程式的緩衝區輸入的描述元欄位。 這個值會繫結的資料型別 *\*TargetValuePtr*緩衝區描述項欄位。 (SQL_ARD_TYPE 尚未進入的呼叫**SQLBindCol**或**SQLBindParameter**因為繫結的緩衝區類型已經繫結至 SQL_DESC_TYPE 和 SQL_DESC_CONCISE_TYPE 欄位，而且可以變更在任何時間變更這些欄位。）  
  
 SQL_ARD_TYPE 類型識別項可以用來指定非預設值的開頭有效位數和間隔資料型別，秒數有效位數和類型的有效位數和小數位數 SQL_C_NUMERIC 資料值。 如需詳細資訊，請參閱[覆寫預設前置和 Interval 資料類型的秒數有效位數](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md)和[覆寫預設有效位數和小數位數的數值資料型別](../../../odbc/reference/appendixes/overriding-default-precision-and-scale-for-numeric-data-types.md)稍後在本附錄中。
