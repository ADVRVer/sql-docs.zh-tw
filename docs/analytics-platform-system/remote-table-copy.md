---
title: "遠端資料表副本 (SQL Server PDW)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e00d948f-fede-4d41-a45d-67134770ce37
caps.latest.revision: "23"
ms.openlocfilehash: 0da111351c260ce4908c36cacdbe9fdbcad21b70
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="remote-table-copy"></a>遠端資料表複製
描述如何將資料表從 SQL Server PDW 資料庫複製到遠端 （非應用裝置） SMP SQL Server 資料庫時，用於遠端資料表複製功能。 使用 SQL Server PDW 啟用中樞和支點案例的遠端資料表副本。  
  
## <a name="BasicsPDE"></a>了解 SQL Server PDW 遠端資料表複製  
遠端資料表複製是啟用將 SQL SELECT 陳述式的結果複製到 SMP 資料庫的資料表中的中樞和支點案例的 SQL Server PDW 的功能。 使用起始遠端資料表複製[建立遠端 TABLE AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md)陳述式。  
  
## <a name="BasicsPrerequisites"></a>使用遠端資料表複製的需求  
符合這些條件時，您可以使用從 SQL Server PDW 」 至 SQL Server 資料庫中的遠端資料表複製到複製資料表：  
  
-   目的地資料庫必須是 Microsoft® SQL Server® Microsoft Windows® 系統可以連線到 SQL Server PDW 應用裝置，但不是位於應用裝置內的伺服器上執行的執行個體。 遠端 SQL Server 可以連接到 SQL Server PDW 使用 InfiniBand 網路或透過乙太網路。  
  
-   要複製的資料必須可使用單一的有效 SQL Server PDW 選取[選取](../t-sql/queries/select-transact-sql.md)陳述式。  
  
-   目的地伺服器必須是在非應用裝置的伺服器。 資料無法直接從一個工具複製到另一個使用中的指示本主題。  
  
-   目的地伺服器必須可以存取應用裝置的 Infiniband 網路上的所有節點。  
  
## <a name="ConfigureRemote"></a>設定遠端資料表的副本  
若要使用遠端資料表的複本，您必須購買並設定 Windows server 的 Windows 伺服器上，設定 SQL Server 及設定 SQL Server PDW。 您可以使用下列連結來執行下列三個設定步驟。  
  
1.  [設定要接收遠端資料表的副本使用 InfiniBand 外部 Windows 系統](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md)  
  
2.  [外部 SMP SQL 伺服器設定為接收遠端資料表的副本](configure-an-external-smp-sql-server-to-receive-remote-table-copies.md)  
  
3.  [設定為遠端資料表複製的 SQL Server PDW](configure-sql-server-pdw-for-remote-table-copies.md)  
  
## <a name="PerformRemote"></a>執行遠端資料表複製  
若要執行的遠端資料表的複本，使用[建立遠端 TABLE AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) SQL 陳述式。 範例隨附於 CREATE REMOTE TABLE 主題。  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
