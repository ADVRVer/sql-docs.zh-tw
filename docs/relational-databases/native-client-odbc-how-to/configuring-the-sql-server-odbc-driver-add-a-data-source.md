---
title: "加入資料來源 (ODBC) |Microsoft 文件"
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 69b2056a8d9b51f6e75eb68a3323665fcc956a92
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="configuring-the-sql-server-odbc-driver---add-a-data-source"></a>設定 SQL Server ODBC 驅動程式-加入資料來源
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  在搭配 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更新版本使用 ODBC 應用程式以前，您必須知道如何在舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上升級目錄預存程序的版本，以及加入、刪除和測試資料來源。  
  
  您可以加入資料來源使用 ODBC 管理員，以程式設計方式 (使用[SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md))，或藉由建立檔案。  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>使用 ODBC 管理員加入資料來源  
  
1.  從**控制台**，存取**系統管理工具**然後**ODBC 資料來源 （64 位元）**或**ODBC 資料來源 （32 位元）**. 或者，您可以叫用 odbcad32.exe。  
  
2.  按一下**使用者 DSN**，**系統 DSN**，或**檔案 DSN**索引標籤，然後再按一下**新增**。  
  
3.  按一下**SQL Server**，然後按一下 **完成**。  
  
4.  完成中的步驟**建立新的資料來源至 SQL Server**精靈。  
  
### <a name="to-add-a-data-source-programmatically"></a>以程式設計方式加入資料來源  
  
1.  呼叫[SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)與第二個參數設定為 ODBC_ADD_DSN 或 ODBC_ADD_SYS_DSN。  
  
### <a name="to-add-a-file-data-source"></a>加入檔案資料來源  
  
1.  呼叫[SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md)的 savefile = file_name 參數的連接字串中。 如果連接成功，ODBC 驅動程式會利用 SAVEFILE 參數所指向位置中的連接參數建立檔案資料來源。  
  
## <a name="see-also"></a>請參閱＜  
[刪除資料來源 &#40; ODBC &#41;](../../relational-databases/native-client-odbc-how-to/configuring-the-sql-server-odbc-driver-delete-a-data-source.md)    
  
  
