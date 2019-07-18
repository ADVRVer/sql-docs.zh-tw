---
title: 使用快照隔離 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], snapshot isolation
- SQLNCLI, snapshot isolation
- isolation levels [SQL Server], snapshot
- DBPROPSET_SESSION property set
- DBDROPSET_DATASOURCEINFO property set
- snapshot isolation [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, snapshot isolation
- SQL Server Native Client ODBC driver, snapshot isolation
- SQL Server Native Client, snapshot isolation
- SQLGetInfo function
- concurrency [SQL Server Native Client]
- SQLSetConnectAttr function
ms.assetid: 39e87eb1-677e-45dd-bc61-83a4025a7756
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e6af092a0c78264ac359ba2cda32527f4ef62d8e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915265"
---
# <a name="working-with-snapshot-isolation"></a>使用快照隔離
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 引進了新的「快照」隔離等級，目的是增強線上交易處理 (OLTP) 應用程式的並行存取。 在舊版的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，並行存取完全以鎖定為基礎，因此導致某些應用程式發生封鎖及死結問題。 快照集隔離相依於對資料列版本設定的增強功能，目的是藉由避免發生讀取器-寫入器封鎖的案例來改善效能。  
  
 在快照隔離下啟動的交易會根據交易啟動的時間而讀取資料庫快照。 其結果之一，就是索引鍵集、動態和靜態伺服器資料指標在快照交易內容內開啟時，其行為與在可序列化交易內開啟的靜態資料指標非常類似。 不過，當資料指標開啟時，快照隔離等級並不會鎖定，因而可能減少伺服器上發生封鎖的機會。  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB 提供者  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者具備增強功能，利用中所引進的快照集隔離[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]。 這些增強功能包括對 DBPROPSET_DATASOURCEINFO 和 DBPROPSET_SESSION 屬性集所做的變更。  
  
### <a name="dbpropsetdatasourceinfo"></a>DBPROPSET_DATASOURCEINFO  
 DBPROPSET_DATASOURCEINFO 屬性集已變更，現藉由加入用於 DBPROP_SUPPORTEDTXNISOLEVELS 屬性中的 DBPROPVAL_TI_SNAPSHOT 值來支援快照隔離等級。 這個新值代表不論資料庫上是否啟用版本控制，快照隔離等級都受到支援。 下列是 DBPROP_SUPPORTEDTXNISOLEVELS 值的清單：  
  
|屬性識別碼|描述|  
|-----------------|-----------------|  
|DBPROP_SUPPORTEDTXNISOLEVELS|類型：VT_I4<br /><br /> R/W:唯讀屬性<br /><br /> 描述：位元遮罩，指定受支援之交易隔離等級。 下列零或多個項目的組合：<br /><br /> DBPROPVAL_TI_CHAOS<br /><br /> DBPROPVAL_TI_READUNCOMMITTED<br /><br /> DBPROPVAL_TI_BROWSE<br /><br /> DBPROPVAL_TI_CURSORSTABILITY<br /><br /> DBPROPVAL_TI_READCOMMITTED<br /><br /> DBPROPVAL_TI_REPEATABLEREAD<br /><br /> DBPROPVAL_TI_SERIALIZABLE<br /><br /> DBPROPVAL_TI_ISOLATED<br /><br /> DBPROPVAL_TI_SNAPSHOT|  
  
### <a name="dbpropsetsession"></a>DBPROPSET_SESSION  
 DBPROPSET_SESSION 屬性集已變更，現藉由加入用於 DBPROP_SESS_AUTOCOMMITISOLEVELS 屬性中的 DBPROPVAL_TI_SNAPSHOT 值來支援快照隔離等級。 這個新值代表不論資料庫上是否啟用版本控制，快照隔離等級都受到支援。 下列是 DBPROP_SESS_AUTOCOMMITISOLEVELS 值的清單：  
  
|屬性識別碼|描述|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|類型：VT_I4<br /><br /> R/W:唯讀屬性<br /><br /> 描述：指定的位元遮罩，指出在自動認可模式中的交易隔離等級。 在此位元遮罩中設定的值，與針對 DBPROP_SUPPORTEDTXNISOLEVELS 而設定的值相同。|  
  
> [!NOTE]  
>  如果使用早於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 版本時設定 DBPROPVAL_TI_SNAPSHOT，就會發生 DB_S_ERRORSOCCURRED 或 DB_E_ERRORSOCCURRED 錯誤。  
  
 如需如何在交易中支援快照隔離的資訊，請參閱[支援本機交易](../../../relational-databases/native-client-ole-db-transactions/supporting-local-transactions.md)。  
  
## <a name="sql-server-native-client-odbc-driver"></a>SQL Server Native Client ODBC 驅動程式  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式提供支援對快照集隔離的增強功能來[SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)並[SQLGetInfo](../../../relational-databases/native-client-odbc-api/sqlgetinfo.md)函式。  
  
### <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 **SQLSetConnectAttr**函數現支援 SQL_COPT_SS_TXN_ISOLATION 屬性。 將 SQL_COPT_SS_TXN_ISOLATION 設定為 SQL_TXN_SS_SNAPSHOT 代表交易會在快照隔離等級之下發生。  
  
### <a name="sqlgetinfo"></a>SQLGetInfo  
 [SQLGetInfo](../../../relational-databases/native-client-odbc-api/sqlgetinfo.md)函數現支援 SQL_TXN_SS_SNAPSHOT 值已加入至 SQL_TXN_ISOLATION_OPTION 資訊類型。  
  
 如需如何在交易中支援快照隔離的資訊，請參閱[資料指標交易隔離等級](../../../relational-databases/native-client-odbc-cursors/properties/cursor-transaction-isolation-level.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Native Client 功能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [資料列集屬性和行為](../../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
  
