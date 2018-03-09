---
title: "SQLBrowseConnect |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLBrowseConnect function
ms.assetid: 57faf388-c7ca-4696-9845-34e0a10cc5f7
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8af521c2bd56d8d66386be324477b7f094052d73
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2018
---
# <a name="sqlbrowseconnect"></a>SQLBrowseConnect
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLBrowseConnect**使用關鍵字可分類成三個層級的連接資訊。 下表針對每個關鍵字指出是否傳回有效值清單以及關鍵字是否為選擇性。  
  
## <a name="level-1"></a>層級 1  
  
|關鍵字|傳回清單？|選擇性？|Description|  
|-------------|--------------------|---------------|-----------------|  
|DSN|해당 사항 없음|否|所傳回的資料來源名稱**SQLDataSources**。 如果使用 DRIVER 關鍵字，就無法使用 DSN 關鍵字。|  
|DRIVER|해당 사항 없음|否|Microsoft® [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式名稱是 {[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11}。 如果使用 DSN 關鍵字，就無法使用 DRIVER 關鍵字。|  
  
## <a name="level-2"></a>層級 2  
  
|關鍵字|傳回清單？|選擇性？|Description|  
|-------------|--------------------|---------------|-----------------|  
|SERVER|是|否|事件來源所在之網路上的伺服器名稱。 可以輸入 "(local)" 這個詞彙做為伺服器，在這種情況下可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的本機複本，即使這是非網路的版本。|  
|UID|否|是|使用者登入識別碼。|  
|PWD|否|是 (依使用者而定)|使用者指定的密碼。|  
|APP|否|是|名稱的應用程式呼叫**SQLBrowseConnect**。|  
|WSID|否|是|工作站識別碼。 一般而言，這是應用程式執行所在之電腦的網路名稱。|  
  
## <a name="level-3"></a>層級 3  
  
|關鍵字|傳回清單？|選擇性？|Description|  
|-------------|--------------------|---------------|-----------------|  
|DATABASE|是|是|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的名稱。|  
|LANGUAGE|是|是|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所用的國家語言。|  
  
 **SQLBrowseConnect**會忽略儲存在 ODBC 資料來源定義中的 DATABASE 和 LANGUAGE 關鍵字的值。 如果資料庫或連接字串中指定的語言傳遞到**SQLBrowseConnect**無效， **SQLBrowseConnect**傳回 SQL_NEED_DATA 和層級 3 連接屬性。  
  
 下列屬性，而這藉由呼叫設定[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)，判斷所傳回的結果集**SQLBrowseConnect**。  
  
|Attribute|Description|  
|---------------|-----------------|  
|SQL_COPT_SS_BROWSE_CONNECT|如果設定為 SQL_MORE_INFO_YES，則**SQLBrowseConnect**傳回伺服器屬性的擴充的字串。<br /><br /> 下列是所傳回之擴充字串的範例**SQLBrowseConnect**:<br /><br /> <br /><br /> `ServerName\InstanceName;Clustered:No;Version:8.00.131`<br /><br /> <br /><br /> 在這個字串中，分號是用來區隔伺服器相關資訊的不同部分， 逗號則是用來區隔不同的伺服器執行個體。|  
|SQL_COPT_SS_BROWSE_SERVER|如果指定伺服器名稱，則**SQLBrowseConnect**會傳回指定之伺服器的資訊。 如果 SQL_COPT_SS_BROWSE_SERVER 設定為 NULL， **SQLBrowseConnect**傳回網域中的所有伺服器的資訊。<br /><br /> <br /><br /> 請注意，因為網路問題、 **SQLBrowseConnect**可能未收到所有伺服器及時的回應。 因此，每個要求所傳回的伺服器清單可能各不相同。|  
|SQL_COPT_SS_BROWSE_CACHE_DATA|當 SQL_COPT_SS_BROWSE_CACHE_DATA 屬性是設定為 SQL_CACHE_DATA_YES 時，您可以在緩衝區長度不足以容納結果時，以片段的方式提取資料。 SQLBrowseConnect Columnsize 引數中指定這個長度。<br /><br /> 當有更多資料可用時，會傳回 SQL_NEED_DATA。 當沒有其他要擷取的資料時，會傳回 SQL_SUCCESS。<br /><br /> 預設為 SQL_CACHE_DATA_NO。|  
  
## <a name="sqlbrowseconnect-support-for-high-availability-disaster-recovery"></a>高可用性/災害復原的 SQLBrowseConnect 支援  
 如需有關使用**SQLBrowseConnect**連接到[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]叢集，請參閱[SQL Server Native Client Support for High Availability，Disaster Recovery](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)。  
  
## <a name="sqlbrowseconnect-support-for-service-principal-names-spns"></a>服務主要名稱 (SPN) 的 SQLBrowseConnect 支援  
 開啟連接時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 會將 SQL_COPT_SS_MUTUALLY_AUTHENTICATED 和 SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD 設定為開啟連接所使用的驗證方法。  
  
 如需有關 Spn 的詳細資訊，請參閱[服務主要名稱 &#40;Spn &#41;用戶端連接 &#40; ODBC &#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="change-history"></a>變更記錄  
  
|更新的內容|  
|---------------------|  
|已記載 SQL_COPT_SS_BROWSE_CACHE_DATA。|  
  
## <a name="see-also"></a>另請參閱  
 [SQLBrowseConnect 函數](http://go.microsoft.com/fwlink/?LinkId=59329)   
 [ODBC API 實作詳細資料](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
