---
description: 'IDBProperties (Native Client OLE DB 提供者) '
title: IDBProperties (Native Client OLE DB 提供者) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d8b1e72d69d047f2fee77db933f9acb447724035
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91866742"
---
# <a name="idbproperties-native-client-ole-db-provider"></a>IDBProperties (Native Client OLE DB 提供者) 
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  OLE DB 標準規格允許提供者將 VT_EMPTY 指定給 **DBPROPINFO::vValues**。 但是， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 當您呼叫 **IDBProperties：： GetPropertyInfo** 搭配 **DBPROPSET_ROWSETALL** 來取出資料列集屬性時，Native Client OLE DB 一律會傳回 VT_EMPTY。  
  
## <a name="see-also"></a>另請參閱  
 [介面 &#40;OLE DB&#41;](./sql-server-native-client-ole-db-interfaces.md)  
  
