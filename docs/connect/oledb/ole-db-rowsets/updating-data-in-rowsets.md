---
title: 更新資料列集中 |Microsoft 文件
description: 更新資料集中的資料列集使用的 SQL Server 的 OLE DB 驅動程式
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
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, updating data
- OLE DB Driver for SQL Server, data updates
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 009c6023dc1905ac724287790c1b26a4bfcf87d3
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689901"
---
# <a name="updating-data-in-rowsets"></a>更新資料列集中的資料
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  SQL Server 更新 OLE DB 驅動程式[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]時取用者更新包含之資料的可修改資料列集資料。 當取用者要求支援時，會建立可修改的資料列集**IRowsetChange**或**IRowsetUpdate**介面。  
  
 所有 OLE DB 驅動程式供 SQL Server 可修改的資料列集使用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]資料指標來支援資料列集。 資料列集屬性 DBPROP_LOCKMODE 會改變資料指標中的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 並行控制行為，並且決定可更新資料列集中的資料列集資料列擷取以及資料完整性錯誤產生的行為。  
  
 SQL Server 的 OLE DB 驅動程式支援資料列同步處理之前或之後更新。  
  
> [!NOTE]  
>  IRowChange::SetColumns 可用來設定資料列物件的一或多個具名資料行的值。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [更新 SQL Server 資料指標中的資料](../../oledb/ole-db-rowsets/updating-data-in-sql-server-cursors.md)  
  
-   [重新同步處理的資料列](../../oledb/ole-db-rowsets/updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>另請參閱  
 [資料列集](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
