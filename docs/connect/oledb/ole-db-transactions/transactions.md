---
title: 交易 | Microsoft Docs
description: OLE DB Driver for SQL Server 中的交易
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 64a05f57c40027a4db448a987d32f77d62f0a837
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86011233"
---
# <a name="transactions"></a>交易
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server 會實作本機交易支援。 取用者可以使用 Microsoft 分散式交易協調器 (MS DTC) 來使用分散式或協調的交易。 如果取用者需要跨多個工作階段的交易控制，OLE DB Driver for SQL Server 可以聯結由 MS DTC 所起始和維護的交易。  
  
 根據預設，OLE DB Driver for SQL Server 會使用自動認可交易模式，在此模式中，取用者工作階段上每個離散的動作都會針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體而構成完整的交易。 OLE DB Driver for SQL Server 自動認可模式為本機，而自動認可交易絕不會跨越一個以上的工作階段。  
  
 OLE DB Driver for SQL Server 會公開 **ITransactionLocal** 介面，讓取用者在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的單一連接上，明確地使用並隱含地啟動交易。 OLE DB Driver for SQL Server 不支援巢狀本機交易。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [支援本機交易](../../oledb/ole-db-transactions/supporting-local-transactions.md)  
  
-   [支援分散式交易](../../oledb/ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [隔離等級 &#40;OLE DB&#41;](../../oledb/ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB Driver for SQL Server 程式設計](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
