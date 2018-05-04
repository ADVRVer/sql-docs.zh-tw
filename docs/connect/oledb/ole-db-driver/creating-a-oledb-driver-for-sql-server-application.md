---
title: SQL Server 應用程式建立 OLE DB 驅動程式 |Microsoft 文件
description: 建立 OLE DB 驅動程式的 SQL Server 應用程式
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, application creation
- applications [OLE DB Driver for SQL Server]
- OLE DB, creating applications
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 697e3f5e563c360f744e5703ca74b3b5557bfbf8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="creating-an-ole-db-driver-for-sql-server-application"></a>SQL Server 應用程式建立 OLE DB 驅動程式
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  建立 OLE DB 驅動程式的 SQL Server 應用程式包含下列步驟：  
  
1.  建立與資料來源的連接。  
  
2.  執行命令。  
  
3.  處理結果。  
  
> [!NOTE]  
>  盡可能使用 Windows 驗證。 如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。 請避免將認證儲存在檔案中。 如果您必須保存認證，您應該先加密它們與[Win32 cryptoAPI](http://go.microsoft.com/fwlink/?LinkId=9504)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [建立資料來源的連接](../../oledb/ole-db-driver/establishing-a-connection-to-a-data-source.md)  
  
-   [執行命令](../../oledb/ole-db-driver/executing-a-command.md)  
  
-   [處理結果](../../oledb/ole-db-driver/processing-results.md)  
  
-   [關於 OLE DB 屬性](../../oledb/ole-db-driver/about-ole-db-properties.md)  
  
-   [在 OLE DB Driver for SQL Server 中使用具有 OLE DB 的 OUTPUT 子句](../../oledb/ole-db-driver/using-the-output-clause-with-ole-db-in-oledb-driver-for-sql-server.md)  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB Driver for SQL Server 程式設計](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
