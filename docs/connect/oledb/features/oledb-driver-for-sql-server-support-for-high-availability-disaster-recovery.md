---
title: 高可用性、 災害復原的 SQL Server 支援的 OLE DB 驅動程式 |Microsoft 文件
description: OLE DB 驅動程式的 SQL Server 支援高可用性、 災害復原
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 9e2d236030dd77f2902e2e13575cc4aea2bc39ae
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2018
---
# <a name="ole-db-driver-for-sql-server-support-for-high-availability-disaster-recovery"></a>高可用性、 災害復原的 SQL Server 支援的 OLE DB 驅動程式
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  本主題討論的 SQL Server 支援的 OLE DB 驅動程式 (在中加入[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]) 的[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]。 如需 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 的詳細資訊，請參閱[可用性群組接聽程式、用戶端連接性及應用程式容錯移轉 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)、[建立及設定可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md)、[容錯移轉叢集和 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md) 和[使用中次要：可讀取的次要複本 &#40;AlwaysOn 可用性群組&#41;](../../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)。  
  
 您可以在連接字串中指定給定可用性群組的可用性群組接聽程式。 如果 SQL Server 應用程式 OLE DB 驅動程式連接到容錯移轉可用性群組中的資料庫，則原始連接會中斷，和應用程式必須開啟新連接，才能在容錯移轉之後繼續工作。  
  
 如果您未連接到可用性群組接聽程式，而且如果多個 IP 位址與主機名稱相關聯，OLE DB 驅動程式的 SQL Server 會循序逐一查看所有與 DNS 項目相關聯的 IP 位址。 如果 DNS 伺服器所傳回的第一個 IP 位址未繫結至任何網路介面卡 (NIC)，這項作業可能會很費時。 連接到可用性群組接聽程式時，OLE DB 驅動程式的 SQL Server 會嘗試平行建立的所有 IP 位址的連接，如果連接嘗試成功，驅動程式將會捨棄任何暫止的連接嘗試。  
  
> [!NOTE]  
>  增加連接逾時並實作連接重試邏輯可提高應用程式連接到可用性群組的機率。 此外，因為連接可能會由於可用性群組容錯移轉而失敗，所以您應該實作連接重試邏輯，並重試失敗的連接，直到重新連接為止。  
  
## <a name="connecting-with-multisubnetfailover"></a>使用 MultiSubnetFailover 進行連接  
 在連接到 SQL Server 2012 可用性群組接聽程式或 SQL Server 2012 容錯移轉叢集執行個體時，永遠指定 **MultiSubnetFailover=Yes**。 **MultiSubnetFailover**啟用更快速的容錯移轉的所有可用性群組和容錯移轉叢集 SQL Server 2012 中執行個體，並大幅縮短單一和多重子網路 Alwayson 拓撲的容錯移轉時間。 在多重子網路容錯移轉期間，用戶端會平行嘗試連接。 子網路容錯移轉期間，OLE DB 驅動程式的 SQL Server 會積極重試 TCP 連接。  
  
 **MultiSubnetFailover**連接屬性表示應用程式正在可用性群組或容錯移轉叢集執行個體中部署，而且 SQL Server 的 OLE DB 驅動程式會嘗試在連接到資料庫主要[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體來嘗試連接到所有 IP 位址。 為連接指定 **MultiSubnetFailover=Yes** 時，用戶端會重試 TCP 連接，其速度比作業系統的預設 TCP 重新傳輸間隔更快。 這可讓容錯移轉後更快重新連線的 Alwayson 可用性群組或一律在容錯移轉叢集執行個體，而且適用於單一-和多重子網路可用性群組和容錯移轉叢集執行個體。  
  
 如需有關連接字串關鍵字的詳細資訊，請參閱[搭配 OLE DB 驅動程式的 SQL Server 中使用連接字串關鍵字](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)。  
  
 當連接到可用性群組接聽程式或容錯移轉叢集執行個體以外的某個項目時，指定 **MultiSubnetFailover=Yes** 將會產生負面效能影響，而且不支援這樣的處理方式。  
  
 請使用下列指導方針，連接到可用性群組或容錯移轉叢集執行個體中的伺服器：  
  
-   如果在連接到單一子網路或多重子網路時使用 **MultiSubnetFailover** 連接屬性，則會提高兩者的效能。  
  
-   若要連接到可用性群組，在連接字串中指定可用性群組的可用性群組接聽程式做為伺服器。  
  
-   連接到設定超過 64 個 IP 位址的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體會導致連接失敗。  
  
-   根據驗證的類型，使用 **MultiSubnetFailover** 連接屬性之應用程式的行為不會受到影響：[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證、Kerberos 驗證或 Windows 驗證。  
  
-   您可以增加 **loginTimeout** 的值，以容納容錯移轉時間並減少應用程式連接重試次數。  
  
-   不支援分散式交易。  
  
 如果唯讀路由不在作用中，在下列狀況下，連接到可用性群組中的次要複本位置將會失敗：  
  
1.  如果未設定次要複本位置接受連接。  
  
2.  如果應用程式使用 **ApplicationIntent=ReadWrite**，而且已針對唯讀存取設定次要複本位置。  
  
 如果設定主要複本拒絕唯讀工作負載，而且連接字串包含 **ApplicationIntent=ReadOnly**，則連接會失敗。  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>從資料庫鏡像升級到使用多子重網路叢集  
 如果連接字串中有 **MultiSubnetFailover** 和 **Failover_Partner** 連接關鍵字，則會發生連接錯誤。 如果使用 **MultiSubnetFailover** 而且 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 傳回容錯移轉夥伴回應，指出它是資料庫鏡像配對的一部分，也會發生錯誤。  
  
 如果您升級 SQL Server 應用程式 OLE DB 驅動程式目前使用資料庫鏡像的多重子網路案例，您應該移除**Failover_Partner**連接屬性並將它取代為**MultiSubnetFailover**設**是**和可用性群組接聽程式取代連接字串中的伺服器名稱。 如果連接字串使用 **Failover_Partner** 和 **MultiSubnetFailover=Yes**，驅動程式會發生錯誤。 不過，如果連接字串使用 **Failover_Partner** 和 **MultiSubnetFailover=No** (或 **ApplicationIntent=ReadWrite**)，應用程式就會使用資料庫鏡像。  
  
 如果可用性群組中的主要資料庫使用資料庫鏡像，而且如果在連接到主要資料庫 (而不是可用性群組接聽程式) 的連接字串中使用 **MultiSubnetFailover=Yes**，驅動程式會傳回錯誤。  
  
## <a name="specifying-application-intent"></a>指定應用程式意圖  
 當**ApplicationIntent = ReadOnly**，用戶端會連線到啟用 Always On 的資料庫時要求讀取工作負載。 伺服器會在連接時和在 USE 資料庫陳述式期間，只針對啟用 AlwaysOn 的資料庫強制執行此意圖。  
  
 **ApplicationIntent** 關鍵字不適用於舊版唯讀資料庫。  
  
 資料庫可以允許或不允許目標 Alwayson 資料庫上的讀取工作負載。 (作法是使用 **PRIMARY_ROLE** 和 **SECONDARY_ROLE**[!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式的 **ALLOW_CONNECTIONS** 子句。)  
  
 **ApplicationIntent** 關鍵字用於啟用唯讀路由。  
  
## <a name="read-only-routing"></a>唯讀路由  
 唯讀路由是可確保資料庫的唯讀複本之可用性的功能。 若要啟用唯讀路由：  
  
1.  您必須連接到 AlwaysOn 可用性群組的可用性群組接聽程式。  
  
2.  **ApplicationIntent** 連接字串關鍵字必須設為 **ReadOnly**。  
  
3.  可用性群組必須由資料庫管理員設定為啟用唯讀路由。  
  
 使用唯讀路由的多個連接可能不會連接至相同的唯讀複本。 資料庫同步處理的變更或伺服器路由組態的變更，可能會導致用戶端連接至不同的唯讀複本。 若要確保所有唯讀要求連接至相同的唯讀複本，請勿將可用性群組接聽程式傳遞給 **Server** 連接字串關鍵字。 請改為指定唯讀執行個體的名稱。  
  
 唯讀路由可能比連接到主要複本的時間更長，因為唯讀路由先連接到主要複本，再尋找最佳的可讀取次要複本。 因此，您應該增加登入逾時。  

  
## <a name="ole-db"></a>OLE DB  
 SQL Server OLE DB 驅動程式同時支援**ApplicationIntent**和**MultiSubnetFailover**關鍵字。   
  
 兩個的 OLE DB 連接字串關鍵字已加入以支援[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]OLE DB 驅動程式中的 SQL Server:  
  
-   **ApplicationIntent** 
-   **MultiSubnetFailover**  
  
 SQL Server 的 OLE DB 驅動程式中的連接字串關鍵字的相關資訊，請參閱[搭配 OLE DB 驅動程式的 SQL Server 中使用連接字串關鍵字](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)。  

### <a name="application-intent"></a>應用程式的意圖 

 同等的連接屬性如下：  
  
-   **SSPROP_INIT_APPLICATIONINTENT**  
  
-   **DBPROP_INIT_PROVIDERSTRING**  
  
 OLE DB 驅動程式的 SQL Server OLE DB 應用程式可以使用其中一個方法來指定應用程式意圖：  
  
 **Idbinitialize:: Initialize**  
 **IDBInitialize::Initialize** 會使用之前設定的屬性集合來初始化資料來源及建立資料來源物件。 將應用程式意圖指定為提供者屬性或是擴充屬性字串的一部分。  
  
 **Idatainitialize:: Getdatasource**  
 **IDataInitialize::GetDataSource** 會採用可包含 **Application Intent** 關鍵字的輸入連接字串。  
  
 **IDBProperties::GetProperties**  
 **IDBProperties::GetProperties** 會擷取目前在資料來源上設定的屬性值。  您可以透過 DBPROP_INIT_PROVIDERSTRING 屬性和 SSPROP_INIT_APPLICATIONINTENT 屬性擷取 **Application Intent** 值。  
  
 **IDBProperties::SetProperties**  
 若要設定 **ApplicationIntent** 屬性值，請呼叫 **IDBProperties::SetProperties**，其傳入值為 "**ReadWrite**" 或 "**ReadOnly**" 的 **SSPROP_INIT_APPLICATIONINTENT** 屬性，或是值包含 "**ApplicationIntent=ReadOnly**" 或 "**ApplicationIntent=ReadWrite**" 的 **DBPROP_INIT_PROVIDERSTRING** 屬性。  
  
 您可以在 [資料連結屬性] 對話方塊中，[全部] 索引標籤的 [應用程式的意圖屬性] 欄位內指定應用程式意圖。  
  
 當建立隱含連接時，隱含連接將會使用父連接的應用程式意圖設定。 同樣地，從相同資料來源建立的多個工作階段將會繼承資料來源的應用程式意圖設定。  
  
### <a name="multisubnetfailover"></a>MultiSubnetFailover

對等連接屬性是：  
  
-   **SSPROP_INIT_MULTISUBNETFAILOVER**  

SSPROP_INIT_MULTISUBNETFAILOVER 屬性是布林類型。 屬性會接受的值為 VARIANT_TRUE 或 VARIANT_FALSE。

若要設定 MultiSubnetFailover 屬性值，呼叫**idbproperties:: Setproperties** SSPROP_INIT_MULTISUBNETFAILOVER 屬性，其值在傳遞**VARIANT_TRUE**或**VARIANT_FALSE**。 

#### <a name="example"></a>範例

```
DBPROP rgPropMultisubnet;

rgPropMultisubnet.dwPropertyID = SSPROP_INIT_MULTISUBNETFAILOVER;
rgPropMultisubnet.dwOptions = DBPROPOPTIONS_REQUIRED;
rgPropMultisubnet.dwStatus = DBPROPSTATUS_OK;
rgPropMultisubnet.colid = DB_NULLID;
V_VT(&(rgPropMultisubnet.vValue)) = VT_BOOL;
V_BOOL(&(rgPropMultisubnet.vValue)) = VARIANT_TRUE;

DBPROPSET PropSet;

PropSet.rgProperties = &rgPropMultisubnet;
PropSet.cProperties = 1;
PropSet.guidPropertySet = DBPROPSET_SQLSERVERDBINIT;
IDBProperties* pIDBProperties = NULL;
hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void **)&pIDBProperties);
pIDBProperties->SetProperties(1, &PropSet);
```



## <a name="see-also"></a>另請參閱  
 [SQL Server 功能的 OLE DB 驅動程式](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [使用 OLE DB 驅動程式中的連接字串關鍵字，適用於 SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)  
  
  
