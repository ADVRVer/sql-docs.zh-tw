---
title: '使用 irow:: Getcolumns |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
ms.assetid: 1f5d2e03-e6fe-4ea1-b71d-55d02b5d59ae
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 682dc4df928caeefbeff16ea326125bb30d72cdf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47611380"
---
# <a name="using-irowgetcolumns"></a>使用 IRow::GetColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **IRow** 實作可允許以順向循序方式存取資料行。 每次當您存取資料列中的數個資料行時，可以使用 **IRow::GetColumns** 的單一呼叫或是呼叫 **IRow::GetColumns** 多次來存取資料列中的所有資料行。  
  
 **IRow::GetColumns** 的多次呼叫不應該重疊。 例如，如果初次呼叫 **IRow::GetColumns** 會擷取資料行 1、2 和 3，則第二次呼叫 **IRow::GetColumns** 就應該擷取資料行 4、5 和 6。 如果之後的 **IRow::GetColumns** 呼叫重疊，則狀態旗標 (DBCOLUMNACCESS 中的 dwstatus 欄位) 會設定為 DBSTATUS_E_UNAVAILABLE。  
  
## <a name="see-also"></a>另請參閱  
 [使用 IRow 擷取單一資料列](../../relational-databases/native-client-ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
