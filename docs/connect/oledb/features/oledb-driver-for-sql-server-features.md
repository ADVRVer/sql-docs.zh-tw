---
title: OLE DB Driver for SQL Server 功能
description: 了解 OLE DB Driver for SQL Server 所支援的功能，例如資料庫鏡像、非同步作業、Azure Active Directory 等等。
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], features
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c93a622561a7c4384f4e7be3d0e95daf9d46abb
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861457"
---
# <a name="ole-db-driver-for-sql-server-features"></a>OLE DB Driver for SQL Server 功能
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  除了公開 Windows (先前稱為 Microsoft) Data Access Components (WDAC) 的功能之外，OLE DB Driver for SQL Server 也會實作其他許多功能來公開 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能。  
  
## <a name="in-this-section"></a>本節內容    
 [使用資料庫鏡像](../../oledb/features/using-database-mirroring.md)  
 討論 OLE DB Driver for SQL Server 如何支援鏡像資料庫的使用，這是在待命伺服器上保留 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫的複本或鏡像的功能。  
  
 [執行非同步作業](../../oledb/features/performing-asynchronous-operations.md)  
 討論 OLE DB Driver for SQL Server 如何支援非同步作業，這是立即傳回而不在呼叫執行緒上封鎖的功能。  

[使用 Azure Active Directory](using-azure-active-directory.md)  
討論 OLE DB 驅動程式 18.2.1 版中引進的新驗證方法，其具有更安全的預設設定，並允許使用同盟識別身分連線到 Azure SQL Database 的執行個體。

 [使用 Multiple Active Result Set &#40;MARS&#41;](../../oledb/features/using-multiple-active-result-sets-mars.md)  
 討論 OLE DB Driver for SQL Server 如何支援 Multiple Active Result Set (MARS)。 MARS 可讓您使用單一資料庫連接執行與接收多個結果集  
  
 [使用 XML 資料類型](../../oledb/features/using-xml-data-types.md)  
 討論 OLE DB Driver for SQL Server 如何支援 XML 資料類型，這是以 XML 為基礎的資料類型，可以當作資料行類型、變數類型、參數類型或函式傳回型別使用。  
  
 [使用使用者定義型別](../../oledb/features/using-user-defined-types.md)  
 討論 OLE DB Driver for SQL Server 如何支援使用者定義型別 (UDT)，這可讓您將物件和自訂資料結構儲存在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫中，藉以擴充 SQL 類型系統。  
  
 [使用大型實值型別](../../oledb/features/using-large-value-types.md)  
 討論 OLE DB Driver for SQL Server 如何支援大數值資料類型，也就是大型物件資料類型 (LOB)。  
  
 [以程式設計方式變更密碼](../../oledb/features/changing-passwords-programmatically.md)  
 討論 OLE DB Driver for SQL Server 如何支援過期密碼的處理方式，讓密碼現在可以在用戶端上變更，而不需要系統管理員介入。  
  
 [使用快照隔離](../../oledb/features/working-with-snapshot-isolation.md)  
 討論 OLE DB Driver for SQL Server 如何支援資料列版本設定的增強功能，藉由避免發生讀取器-寫入器封鎖的情況來改善效能。  
  
 [使用查詢通知](../../oledb/features/working-with-query-notifications.md)  
 討論 OLE DB Driver for SQL Server 如何支援在資料列集修改時使用取用者通知。  
  
 [執行大量複製作業](../../oledb/features/performing-bulk-copy-operations.md)  
 討論 OLE DB Driver for SQL Server 如何支援大量複製作業，允許將大量資料傳送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料表或檢視表，或從中傳出。  
  
 [使用加密而不需驗證](../../oledb/features/using-encryption-without-validation.md)  
 討論如何使用 OLE DB Driver for SQL Server 加密傳送到伺服器的資料，而不驗證憑證。  
  
 [資料表值參數 &#40;OLE DB Driver for SQL Server&#41;](../../oledb/features/table-valued-parameters-oledb-driver-for-sql-server.md)  
 討論 OLE DB Driver for SQL Server 對資料表值參數的支援。  
  
 [大型 CLR 使用者定義型別](../../oledb/features/large-clr-user-defined-types.md)  
 討論大型 Common Language Runtime (CLR) 使用者定義型別 (UDT) 的支援。  
  
 [FILESTREAM 支援](../../oledb/features/filestream-support.md)  
 討論 OLE DB Driver for SQL Server 對已增強 FILESTREAM 功能的支援。  
  
 [用戶端連線中的服務主要名稱 &#40;SPN&#41; 支援](../../oledb/features/service-principal-name-spn-support-in-client-connections.md)  
 討論如何擴充服務主要名稱 (SPN) 的支援以便跨所有通訊協定進行相互驗證。  
  
 [OLE DB Driver for SQL Server 中支援疏鬆資料行](../../oledb/features/sparse-columns-support-in-oledb-driver-for-sql-server.md)  
 討論 OLE DB Driver for SQL Server 對疏鬆資料行的支援。  
  
 [日期和時間改善](../../oledb/features/date-and-time-improvements.md)  
 討論已在 OLE DB Driver for SQL Server 中新增對新日期和時間資料類型的支援。  
  
 [中繼資料探索](../../oledb/features/metadata-discovery.md)  
 討論在 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 內所做的中繼資料探索改進。  
  
 [OLE DB Driver for SQL Server 中支援 UTF-16](../../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)  
 討論 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中導入的行為變更。 如果您在繫結資料行結果或輸出參數時提供固定長度的緩衝區、**wchar** 字元在終止字元成為代理字組的高 Surrogate 字碼指標之前寫入緩衝區，而且下一個 **wchar** 字元是低 Surrogate 字碼指標，OLE DB Driver for SQL Server 就不會將高 Surrogate 字碼指標新增至緩衝區。  
 
 [OLE DB Driver for SQL Server 中的 UTF-8 支援](../../oledb/features/utf-8-support-in-oledb-driver-for-sql-server.md)  
 討論在使用 UTF-8 編碼的資料時，使用者應採取的 UTF-8 伺服器編碼和設定預防措施的支援。
  
 [OLE DB Driver for SQL Server 支援高可用性、災害復原](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  
 討論如何設定應用程式以利用 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中新增的高可用性災害復原功能。  
  
 [存取擴充事件記錄檔中的診斷資訊](../../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)  
 討論可讓您存取信號緩衝區和 XEvents 記錄檔中之診斷資訊的 OLE DB Driver for SQL Server 及資料追蹤增強功能。  
  
 [OLE DB Driver for SQL Server 支援 LocalDB](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)  
 討論 OLE DB Driver for SQL Server 對 LocalDB 功能的支援。  
  
 [使用透明網路 IP 解析](../../oledb/features/using-transparent-network-ip-resolution.md)  
 討論 OLE DB Driver for SQL Server 如何在容錯移轉叢集中支援透明網路 IP 解析。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB Driver for SQL Server](../../oledb/oledb-driver-for-sql-server.md)      
 [OLE DB 的使用說明主題](../../oledb/ole-db-how-to/ole-db-how-to-topics.md)   
 [安裝 OLE DB Driver for SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md)  
  
  
