---
title: SQL Server Native Client ODBC 資料來源 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, about data sources
- ODBC data sources, names
- data sources [SQL Server Native Client]
- names [ODBC]
- ODBC applications, data sources
- SQL Server Native Client ODBC driver, data sources
- ODBC data sources
ms.assetid: a6a50fd0-d439-43fd-b76f-16ec02f478c5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 318ff6f9abf54e4c8e15e623bde7d5007a747eef
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47717626"
---
# <a name="sql-server-native-client-odbc-data-sources"></a>SQL Server Native Client ODBC 資料來源
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料來源名稱 (DSN) 會識別 ODBC 資料來源，其中包含 ODBC 應用程式需要連接到特定伺服器之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的所有資訊。 有兩個方式可以定義 ODBC 資料來源名稱：  
  
-   用戶端電腦上，開啟 控制台 中 系統管理工具，然後按兩下**資料來源 (ODBC)**。 這樣會開啟「ODBC 資料來源管理員」來建立 DSN。  
  
-   在 ODBC 應用程式中，呼叫[SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料來源包含：  
  
-   資料來源的名稱。  
  
-   連接到特定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體所需的任何資訊。  
  
-   在特定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上所使用的預設資料庫 (選擇性)。  
  
-   要使用哪些 ANSI 選項、是否要記錄效能統計資料等等的設定 (選擇性)。  
  
 透過資料來源連接時，不需要 ODBC 應用程式。 不過，應用程式必須提供相同的連接資訊給驅動程式會在 DSN 中找到的 ODBC 連接函數。  
  
## <a name="see-also"></a>另請參閱  
 [與 SQL Server 通訊&#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
