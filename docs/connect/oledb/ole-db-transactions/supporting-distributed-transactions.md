---
title: 支援分散式的交易 |Microsoft Docs
description: 在 OLE DB Driver for SQL Server 的分散式的交易
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- distributed transactions [OLE DB]
- MS DTC
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
- ITransactionJoin interface
- MS DTC, about distributed transaction support
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 9486af5a9dbd4f607f376a5f916e35ace88be872
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43028422"
---
# <a name="supporting-distributed-transactions"></a>支援分散式交易
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server 取用者可以使用 **ITransactionJoin::JoinTransaction** 方法來參與 Microsoft 分散式交易協調器 (MS DTC) 協調的分散式交易。  
  
 MS DTC 會公開 COM 物件，讓用戶端跨各種資料存放區的多個連接，起始並參與協調的交易。 若要起始交易，OLE DB Driver for SQL Server 取用者會使用 MS DTC **ITransactionDispenser**介面。 **ITransactionDispenser** 的 **BeginTransaction** 成員會傳回分散式交易物件的參考。 此參考傳遞至 OLE DB Driver for SQL Server 使用**JoinTransaction**。  
  
 MS DTC 在分散式交易上支援非同步認可和中止。 為取得非同步交易狀態的通知，取用者會實作 **ITransactionOutcomeEvents** 介面，並將介面連接到 MS DTC 交易物件。  
  
 若是分散式交易，OLE DB Driver for SQL Server 會實作 **ITransactionJoin::JoinTransaction** 參數，如下所示。  
  
|參數|Description|  
|---------------|-----------------|  
|*punkTransactionCoord*|MS DTC 交易物件的指標。|  
|*IsoLevel*|忽略 OLE DB Driver for SQL Server。 取用者從 MS DTC 取得交易物件時，會判斷 MS DTC 協調交易的隔離等級。|  
|*IsoFlags*|必須是 0。 如果取用者指定了任何其他值，OLE DB Driver for SQL Server 就會傳回 XACT_E_NOISORETAIN。|  
|*POtherOptions*|如果不是 NULL，OLE DB Driver for SQL Server 會從介面要求選項物件。 OLE DB Driver for SQL Server 會傳回 XACT_E_NOTIMEOUT，如果選項物件的*ulTimeout*成員不是零。 OLE DB Driver for SQL Server 會忽略值*szDescription*成員。|  
  
 這個範例會使用 MS DTC 協調交易。  
  
```  
// Interfaces used in the example.  
IDBCreateSession*       pIDBCreateSession   = NULL;  
ITransactionJoin*       pITransactionJoin   = NULL;  
IDBCreateCommand*       pIDBCreateCommand   = NULL;  
IRowset*                pIRowset            = NULL;  
  
// Transaction dispenser and transaction from MS DTC.  
ITransactionDispenser*  pITransactionDispenser = NULL;  
ITransaction*           pITransaction       = NULL;  
  
    HRESULT             hr;  
  
// Get the command creation interface for the session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
// Get a transaction dispenser object from MS DTC and  
// start a transaction.  
if (FAILED(hr = DtcGetTransactionManager(NULL, NULL,  
    IID_ITransactionDispenser, 0, 0, NULL,  
    (void**) &pITransactionDispenser)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
if (FAILED(hr = pITransactionDispenser->BeginTransaction(  
    NULL, ISOLATIONLEVEL_READCOMMITTED, ISOFLAG_RETAIN_DONTCARE,  
    NULL, &pITransaction)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
  
// Join the transaction.  
if (FAILED(pIDBCreateCommand->QueryInterface(IID_ITransactionJoin,  
    (void**) &pITransactionJoin)))  
    {  
    // Process failure to get an interface, release any references, and  
    // then return.  
    }  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) pITransaction, 0, 0, NULL)))  
    {  
    // Process join failure, release any references, and then return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then abort.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, 0, 0)))  
        {  
        // Get error from failed commit.  
        //  
        // If a distributed commit fails, application logic could  
        // analyze failure and retry. In this example, terminate. The   
        // consumer must resolve this somehow.  
        pITransaction->Abort(NULL, FALSE, FALSE);  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Un-enlist from the distributed transaction by setting   
// the transaction object pointer to NULL.  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) NULL, 0, 0, NULL)))  
    {  
    // Process failure, and then return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>另請參閱  
 [Transactions](../../oledb/ole-db-transactions/transactions.md)  
  
  
