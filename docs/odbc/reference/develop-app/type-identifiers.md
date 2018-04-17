---
title: 輸入識別項 |Microsoft 文件
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
ms.topic: article
helpviewer_keywords:
- data types [ODBC], identifiers
- type identifiers [ODBC]
- identifiers [ODBC], type
- type identifiers [ODBC], about type identifiers
ms.assetid: 1d9fdfa2-e378-44fe-ac66-9743d9bbdd5a
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9a3de97dbf1ce632f1204a2218ead0c7ddd8cdf2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="type-identifiers"></a>類型識別碼
若要描述 SQL 和 C 資料類型，ODBC 定義兩組*鍵入識別碼*。 類型識別項描述 SQL 資料行或 C 緩衝區的類型。 它是**#define**值和通常傳遞做為函式引數或傳回中繼資料中。  
  
 例如，下列呼叫**SQLBindParameter**將 SQL_DATE_STRUCT 類型的變數繫結至 SQL 陳述式中的日期參數。 C 類型識別碼 SQL_C_TYPE_DATE 指定的型別*日期*變數和 SQL 類型識別碼 SQL_TYPE_DATE 指定動態參數的型別。  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER  DateInd = 0;  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &Date, 0, &DateInd);  
```
