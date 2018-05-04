---
title: setTrustStore 方法 (SQLServerDataSource) |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- setTrustStore Method (SQLServerDataSource)
apilocation:
- setTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: bab5485d-4547-426c-adbe-44e2b5702d1d
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 69e1a64ea387f97b9cf478366c3d269002e07cdf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="settruststore-method-sqlserverdatasource"></a>setTrustStore 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  設定憑證 trustStore 檔案的路徑 (包括檔案名稱)。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void setTrustStore(java.lang.String trustStore)  
```  
  
#### <a name="parameters"></a>參數  
 *trustStore*  
  
 A**字串**包含憑證 trustStore 檔案的路徑 （包括檔案名稱）。  
  
## <a name="remarks"></a>備註  
 如果 trustStore 屬性為未指定或設為 null，[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]將會依賴信任管理員 factory 的查閱規則，決定要使用的憑證存放區。 預設的 SunX509 TrustManagerFactory 會嘗試以下列搜尋位置順序，找出信任的資料：  
  
-   1. 由 "javax.net.ssl.trustStore" Java Virtual Machine (JVM) 系統屬性所指定的檔案。  
  
-   2. 「\<java 首頁 >/lib/安全性/jssecacerts"檔案。  
  
-   3. 「\<java 首頁 >/lib/安全性/cacerts"檔案。  
  
 如需詳細資訊，請參閱 Sun Microsystems 網站上的 SunX509 TrustManager 介面文件。  
  
 如果 trustStore 屬性設定為字串或是空字串 ""，驅動程式將會使用該值來找出 trustStore 檔案，以便驗證伺服器 SSL 憑證。  
  
 trustStorePassword 屬性可以隨著 trustStore 屬性一起指定，而其值可用來開啟 trustStore 檔案。 如需詳細資訊，請參閱[setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
