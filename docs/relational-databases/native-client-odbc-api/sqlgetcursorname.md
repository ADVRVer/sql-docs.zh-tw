---
title: SQLGetCursorName |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-api
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetCursorName function
ms.assetid: 3a427a23-28ef-49aa-b9ec-6cab0914bdf3
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 998baf06bb24de7bb3b76f55045ebe16573a72c5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetcursorname"></a>SQLGetCursorName
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  如果應用程式未指定資料指標名稱， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式會產生一個在資料指標產生時應用程式。 應用程式可以使用**SQLGetCursorName**擷取驅動程式定義的資料指標名稱定位 UPDATE 和 DELETE 陳述式。 應用程式不需要呼叫**SQLSetCursorName**利用位於資料操作陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [SQLGetCursorName 函數](http://go.microsoft.com/fwlink/?LinkId=59349)   
 [ODBC API 實作詳細資料](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
