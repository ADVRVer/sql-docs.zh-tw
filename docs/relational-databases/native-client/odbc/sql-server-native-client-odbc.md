---
title: ODBC
description: SQL Server 使用 SQL Server Native Client ODBC 驅動程式支援 ODBC，做為與 SQL Server 通訊之 C 和 c + + 應用程式的原生 API。
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLNCLI, ODBC
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], ODBC
- SQL Server Native Client ODBC driver
- ODBC
- SQL Server Native Client, ODBC
- ODBC, about SQL Server Native Client ODBC driver
ms.assetid: 811d5ba3-a2b8-48c0-adbc-8c91f041f458
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: edf6fee6f271461052da2954dafdcfb6d27de599
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84950208"
---
# <a name="sql-server-native-client-odbc"></a>SQL Server Native Client (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC 是應用程式開發介面 (API) 的標準定義，用於存取關聯式資料庫或索引循序存取方法 (ISAM) 資料庫中的資料。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 透過 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式支援 ODBC 做為其中一個原生應用程式開發介面，來撰寫與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 進行通訊的 C 和 C++ 應用程式。  
  
 使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式撰寫的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 程式會透過 C 函數呼叫，與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 進行通訊。 ODBC 函數的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 專屬版本會在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式中實作。 此驅動程式會將 SQL 陳述式傳遞到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，然後將陳述式的結果傳回到應用程式。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式符合 Microsoft Win32 ODBC 3.51 規格。 此驅動程式支援使用舊版 ODBC，以 ODBC 3.51 規格中定義之方式撰寫的應用程式。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [資料來源名稱和 64 位元作業系統](../../../relational-databases/native-client/odbc/data-source-names-and-64-bit-operating-systems.md)  
  
-   [建立 SQL Server Native Client ODBC 驅動程式應用程式](../../../relational-databases/native-client/odbc/creating-a-driver-application.md)  
  
-   [與 SQL Server &#40;ODBC&#41;通訊](../../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
-   [&#40;ODBC&#41;執行查詢](../../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
-   [&#40;ODBC&#41;處理結果](../../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
-   [&#40;ODBC&#41;使用資料指標](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
-   [&#40;ODBC&#41;執行交易](https://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
-   [處理錯誤與訊息](../../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
-   [執行預存程序](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
-   [使用目錄函式](../../../relational-databases/native-client/odbc/using-catalog-functions.md)  
  
-   [&#40;ODBC&#41;執行大量複製作業](../../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
-   [管理 Text 和 Image 資料行](../../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
-   [分析 ODBC 驅動程式效能](../../../relational-databases/native-client/odbc/profiling-odbc-driver-performance.md)  
  
-   [ODBC&#41;&#40;的資料表值參數](../../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
-   [ODBC&#41;&#40;的日期和時間改善](../../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
-   [&#40;ODBC&#41;的大型 CLR 使用者定義類型](../../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)  
  
-   [FILESTREAM 支援 &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/filestream-support-odbc.md)  
  
-   [用戶端連接 &#40;ODBC&#41; 中的服務主體名稱 &#40;SPN&#41;](../../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)  
  
-   [&#40;ODBC&#41;的稀疏資料行支援](../../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md)  
  
-   [SQL Server Native Client &#40;ODBC&#41; 參考](https://msdn.microsoft.com/library/06b7edee-8636-49d9-9b5c-2c710bf4fa2d)  
  
-   [ODBC 的使用說明主題](../../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Native Client 程式設計](../../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [安裝 SQL Server Native Client](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
  
  
