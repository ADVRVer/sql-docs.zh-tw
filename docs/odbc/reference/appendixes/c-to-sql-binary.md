---
title: SQL 到 C： 二進位 |Microsoft 文件
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
- binary data type [ODBC]
- data conversions from C to SQL types [ODBC], binary
- binary data transfers [ODBC]
- converting data from c to SQL types [ODBC], binary
ms.assetid: 3e9083f3-357b-41aa-833c-2c8aac2226cd
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6d1e7f422829cce804f401ac98083d066e0f67e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32905919"
---
# <a name="c-to-sql-binary"></a>SQL 到 C： 二進位
二進位的 ODBC C 資料類型的識別項是：  
  
 SQL_C_BINARY  
  
 下表顯示 ODBC SQL 資料類型可能會轉換 C 的二進位資料。 如需的資料行和資料表中的詞彙說明，請參閱[轉換資料從 C 到 SQL 資料型別](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)。  
  
|SQL 類型識別碼|測試|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|資料的位元組長度 < = 資料行的位元組長度<br /><br /> 資料的位元組長度 > 資料行的位元組長度|n/a<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|字元長度的資料 < = 資料行的字元長度<br /><br /> 字元資料的長度 > 資料行的字元長度|n/a<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER<br /><br /> SQL_BIGINT<br /><br /> SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE<br /><br /> SQL_BIT SQL_TYPE_DATE<br /><br /> SQL_TYPE_TIME<br /><br /> SQL_TYPE_TIMESTAMP|資料的位元組長度 = SQL 資料長度<br /><br /> 資料 <> SQL 資料長度的位元組長度|n/a<br /><br /> 22003|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|資料長度 < = 資料行長度<br /><br /> 資料長度 > 資料行長度|n/a<br /><br /> 22001|
