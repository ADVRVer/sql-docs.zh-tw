---
title: 釋放陳述式控制代碼 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3da32585644e0bd7d3a572ef2052f387e4d33232
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426727"
---
# <a name="freeing-a-statement-handle"></a>釋放陳述式控制代碼
  重複使用陳述式控制代碼比卸除陳述式控制代碼然後再配置新的陳述式控制代碼更有效率。 針對陳述式控制代碼執行新的 SQL 陳述式之前，應用程式應該確認目前的陳述式設定是否恰當。 這些包括陳述式屬性、參數繫結，以及結果集繫結。 一般而言，參數和結果集的舊的 SQL 陳述式必須藉由呼叫未繫結[SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md)利用 SQL_RESET_PARAMS 和 SQL_UNBIND 選項，並重新繫結為新的 SQL 陳述式。  
  
 當應用程式完成使用陳述式時，它會呼叫[SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md)來釋放陳述式。 請注意， **SQLDisconnect**自動釋放連接上的所有陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [執行查詢&#40;ODBC&#41;](executing-queries-odbc.md)  
  
  
