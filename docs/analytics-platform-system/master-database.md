---
title: Master 資料庫-Parallel Data Warehouse |Microsoft 文件
description: 深入了解 master 平行處理資料倉儲資料庫。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: bf07b9c27e08a49cb0866b177a0ec37fed4528a0
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538538"
---
# <a name="master-database---parallel-data-warehouse"></a>Master 資料庫-Parallel Data Warehouse
SQL Server PDW master 資料庫儲存應用裝置層級登入資訊和資料庫目錄。 它是位於 [控制] 節點上的 SQL Server master 資料庫。 因此，它提供類似的功能與 SQL Server PDW 因為主要提供給 SQL Server。  
  
如需系統資料庫的詳細資訊，請參閱[系統資料庫](system-databases.md)。  
  
## <a name="limitations-and-restrictions"></a>限制事項  
下列清單描述您無法在 SQL Server PDW master 資料庫執行的作業。  
  
您*無法：*  
  
-   執行主要的差異備份。  
  
-   在 master 中建立使用者物件。  
  
-   變更主要的定序。  
  
-   變更主要擁有者。  
  
-   卸除或重新命名主要。  
  
-   修改主機的權限。  
  
-   執行**DBCC SHRINKLOG**。  
  
## <a name="related-tasks"></a>相關工作  
  
|工作|Description|  
|--------|---------------|  
|建立主要的完整備份。|範例：<br /><br />`BACKUP DATABASE master TO backup_directory;`<br /><br />如需詳細資訊，請參閱[BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md)。|  
|還原 master 資料庫|若要還原 master 資料庫，請使用[還原 Master 資料庫](restore-the-master-database.md)組態管理員工具中的頁面。|  
|檢視資料庫的類別目錄資訊。|`SELECT * FROM master.sys.databases;`|  
|檢視全系統登入和權限資訊。|`SELECT * FROM master.sys.server_permissions;`<br /><br />`SELECT * FROM master.sys.server_principals;`<br /><br />`SELECT * FROM master.sys.sql_logins;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
