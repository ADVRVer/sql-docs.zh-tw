---
title: 資料列書簽（Native Client OLE DB 提供者） |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- SQL Server Native Client OLE DB provider, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
ms.assetid: 7d9076f2-bf9c-452e-b816-70371a0c1644
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 149f40d2bc6ddb9313c7e20b76fb6ec7738cd5ce
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942141"
---
# <a name="bookmarks"></a>書籤
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  書籤可讓取用者快速地返回資料列。 取用者可以利用書籤，根據書籤值隨機存取資料列。 書籤資料行在資料列集中為資料行 0。 取用者會將繫結結構的 dwFlag 欄位值設定為 DBCOLUMNSINFO_ISBOOKMARK，表示該資料行會當做書籤使用。 取用者也會將資料列集屬性 DBPROP_BOOKMARKS 設定為 VARIANT_TRUE。 這可讓資料行 0 出現在資料列集中。 然後使用 **IRowsetLocate::GetRowsAt** 方法來擷取資料列，從書籤中指定為位移的資料列開始。  
  
## <a name="see-also"></a>另請參閱  
 [資料列集](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
