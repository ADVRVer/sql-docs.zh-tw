---
title: '使用 irow:: Getcolumns |Microsoft 文件'
description: '使用 irow:: Getcolumns 存取的資料列中的所有資料行'
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [OLE DB Driver for SQL Server]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: be29bec8c92036b6d53a56f4aab8ccdfc8e8c369
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690051"
---
# <a name="using-irowgetcolumns"></a>使用 IRow::GetColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  **IRow**實作可允許以順向循序方式存取資料行。 您可以存取的資料列的單一呼叫中的所有資料行**irow:: Getcolumns**或呼叫**irow:: Getcolumns**多次，每次您存取數個資料列中的資料行。  
  
 多個呼叫**irow:: Getcolumns**不應該重疊。 例如，如果第一次呼叫**irow:: Getcolumns**擷取資料行 1、 2 和 3，第二次呼叫**irow:: Getcolumns**應該呼叫資料行 4、 5 和 6。 如果稍後呼叫**irow:: Getcolumns**重疊，狀態旗標 （DBCOLUMNACCESS 中的 dwstatus 欄位） 會設定為 DBSTATUS_E_UNAVAILABLE。  
  
## <a name="see-also"></a>另請參閱  
 [使用 IRow 擷取單一資料列](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
