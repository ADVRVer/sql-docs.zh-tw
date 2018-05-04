---
title: SQL 一致性層級 |Microsoft 文件
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
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 3529df2c-a09b-4c16-9c60-eae7a06d903a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b9e352aad9c99b56c08767ca57547b9b6594a17
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="sql-conformance-levels"></a>SQL 一致性層級
SQL 92 文法的驅動程式支援的層級由呼叫所傳回的值所表示**SQLGetInfo** SQL_SQL_CONFORMANCE 資訊類型。 這表示驅動程式是否符合以 sql-92 定義的項目、 FIPS 過渡、 中級者、 或全文層級。  
  
 所有的 ODBC 驅動程式必須支援中所述的最低 SQL 文法[SQL 最小文法](../../../odbc/reference/appendixes/sql-minimum-grammar.md)附錄 c: SQL 文法中。 此文法是 sql-92 的項目層級的子集。 驅動程式可能支援其他的 SQL，並為符合 sql-92 項目、 中級者、 或 完整層級，或 FIPS 127-2 過渡期的層級。 給定的層級的 SQL 92 或 FIPS 127-2 符合的驅動程式可支援任何較高的層級中的其他功能，同時又不能完全符合層級。 若要判斷是否支援此功能，應用程式應該呼叫**SQLGetInfo**與適當的資訊類型。 SQL 功能的一致性層級所述的對應資訊類型。 (請參閱[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)函式描述。)
