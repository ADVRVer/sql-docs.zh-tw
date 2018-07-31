---
title: 產生多個資料列集結果的命令 |Microsoft Docs
description: 產生多個資料列集結果的命令
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- OLE DB Driver for SQL Server, commands
- OLE DB Driver for SQL Server, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 579fae980b0f612aa1317407f797be9d1ff02ed3
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2018
ms.locfileid: "39109620"
---
# <a name="commands-generating-multiple-rowset-results"></a>產生多個資料列集結果的命令
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server 可以傳回多個資料列集[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]陳述式。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 陳述式在下列條件下會傳回多個資料列集結果：  
  
-   批次的 SQL 陳述式以單一命令提交。  
  
-   預存程序實作 SQL 陳述式批次。  
  
## <a name="batches"></a>批次  
 OLE DB Driver for SQL Server 將分號字元辨識為 SQL 陳述式的批次分隔符號：  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 以一個批次傳送多個 SQL 陳述式，比分開執行每個 SQL 陳述式的效率高。 傳送單一批次可以減少從用戶端到伺服器的網路往返數。  
  
## <a name="stored-procedures"></a>預存程序  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會針對預存程序中的每個陳述式傳回結果集，所以大部分的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預存程序都會傳回多個結果集。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 IMultipleResults 來處理多個結果集](../../oledb/ole-db-commands/using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a>另請參閱  
 [命令](../../oledb/ole-db-commands/commands.md)  
  
  
