---
title: 游標併發 (ODBC) |微軟文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 309bfb0313adeeb0002910975c0a484461ea608c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298363"
---
# <a name="cursor-concurrency-odbc"></a>資料指標並行 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  資料指標作業跟資料指標類型一樣，會受到應用程式設定之並行選項的影響。 使用[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)SQL_ATTR_CONCURRENCY 選項設定併發選項。 並行類型為：  
  
-   唯讀 (SQL_CONCUR_READONLY)  
  
-   值 (SQL_CONCUR_VALUES)  
  
-   資料列版本 (SQL_CONCUR_ROWVER)  
  
-   鎖定 (SQL_CONCUR_LOCK)  
  
## <a name="see-also"></a>另請參閱  
 [資料指標屬性](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
