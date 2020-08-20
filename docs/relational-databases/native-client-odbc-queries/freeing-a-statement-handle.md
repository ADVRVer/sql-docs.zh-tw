---
description: 釋放陳述式控制代碼
title: 釋放語句控制碼 |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5cf58becc532153617ebcbd3cafc6c89d21b4d00
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499155"
---
# <a name="freeing-a-statement-handle"></a>釋放陳述式控制代碼
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  重複使用陳述式控制代碼比卸除陳述式控制代碼然後再配置新的陳述式控制代碼更有效率。 針對陳述式控制代碼執行新的 SQL 陳述式之前，應用程式應該確認目前的陳述式設定是否恰當。 這些包括陳述式屬性、參數繫結，以及結果集繫結。 一般而言，舊 SQL 語句的參數和結果集必須使用 SQL_RESET_PARAMS 和 SQL_UNBIND 選項來呼叫 [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) ，然後再針對新的 sql 語句進行重新系結，以解除系結。  
  
 當應用程式完成使用語句時，它會呼叫 [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) 來釋放語句。 請注意， **SQLDisconnect** 會自動釋出連接上的所有語句。  
  
## <a name="see-also"></a>另請參閱  
 [&#40;ODBC&#41;執行查詢 ](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
