---
title: 其他非 SQL Server 訂閱者 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- non-SQL Server Subscribers, other types
ms.assetid: 96b8beb9-38e8-4ce4-97ca-c0f8656b73b4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d7f6a8e580d89b9364d6c141dbacac8a405a0667
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892218"
---
# <a name="other-non-sql-server-subscribers"></a>其他非 SQL Server 訂閱者
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  如需 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 支援的非 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者清單，請參閱[非 SQL Server 訂閱者](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)。 本主題包含 ODBC 驅動程式和 OLE DB 提供者需求的資訊。  
  
## <a name="odbc-driver-requirements"></a>ODBC 驅動程式需求  
 ODBC 驅動程式：  
  
-   必須與 ODBC (層級 1) 相容。  
  
-   必須是安全執行緒散發者環境。  
  
-   必須能處理交易 (Transaction capable)。  
  
-   必須支援「資料定義語言」(Data Definition Language，DDL)。  
  
-   不能設定成唯讀。  
  
-   必須支援長資料表名稱，例如 **MSreplication_subscriptions**。  
  
## <a name="replicating-using-ole-db-interfaces"></a>使用 OLE DB 介面進行複寫  
 OLE DB Provider 必須支援下列物件，才能進行異動複寫：  
  
-   **DataSource** 物件  
  
-   **Session** 物件  
  
-   **Command** 物件  
  
-   **Rowset** 物件  
  
-   **Error** 物件  
  
### <a name="datasource-object-interfaces"></a>DataSource 物件介面  
 若要連接到某個資料來源，您必須具備下列介面：  
  
-   **IDBInitialize**  
  
-   **IDBCreateSession**  
  
-   **IDBProperties**  
  
 如果提供者支援 **IDBInfo** 介面，[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 便會使用此介面來擷取引號識別項字元、SQL 陳述式長度上限、資料表和資料行名稱的最大字元數等資訊。  
  
### <a name="session-object-interfaces"></a>Session 物件介面  
 以下是必要的介面：  
  
-   **IDBCreateCommand**  
  
-   **ITransaction**  
  
-   **ITransactionLocal**  
  
-   **IDBSchemaRowset**  
  
### <a name="command-object-interfaces"></a>Command 物件介面  
 以下是必要的介面：  
  
-   **ICommand**  
  
-   **ICommandProperties**  
  
-   **ICommandText**  
  
-   **ICommandPrepare**  
  
-   **IColumnsInfo**  
  
-   **IAccessor**  
  
-   **ICommandWithParameters**  
  
 需要**IAccessor** 才能建立參數存取子 (Accessor)。 如果提供者支援 **IColumnRowset**， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 便會用此介面判斷某個資料行是否為識別欄位。  
  
### <a name="rowset-object-interfaces"></a>Rowset 物件介面  
 以下是必要的介面：  
  
-   **IRowset**  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
 應用程式必須在訂閱資料庫中建立的複寫資料表內，開啟一個資料列集。 **IColumnsInfo** 與 **IAccessor** 是存取此資料列集中的資料所必須具備的。  
  
### <a name="error-object-interfaces"></a>Error 物件介面  
 請使用以下介面來管理錯誤：  
  
-   **IErrorRecords**  
  
-   **IErrorInfo**  
  
 若 OLE DB 提供者支援 **ISQLErrorInfo** ，請使用此介面。  
  
 如需 OLE DB 提供者的詳細資訊，請參閱您 OLE DB 提供者所附的文件。  
  
## <a name="see-also"></a>另請參閱  
 [非 SQL Server 訂閱者](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)  
  
  
