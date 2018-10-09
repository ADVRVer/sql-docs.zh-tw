---
title: 應用程式安全性 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 940879b4-aa0f-41ce-a369-6cfc0e78e01d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 42cf0e2a39a4a08ceab94e5391d3c926fb5751ab
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47775756"
---
# <a name="application-security"></a>應用程式安全性
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  使用 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 時，請務必採取一些預防措施以確保應用程式的安全性。 下列章節會提供保護應用程式時可採取之步驟的相關資訊。  
  
## <a name="using-java-policy-permissions"></a>使用 Java 原則權限  
 使用 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 時，請務必指定 JDBC 驅動程式所需的必要 Java 原則權限。 Java Runtime Environment (JRE) 提供您可在執行階段時使用的延伸安全性模型，以判斷執行緒是否具有資源的存取權限。 安全性原則檔可控制這個存取權限。 原則檔本身是由部署人員和容器的系統管理員所管理，但本主題列出的權限則會影響 JDBC 驅動程式的功能。  
  
 原則檔中典型的權限看起來如下：  
  
```  
// Example policy file entry.  
grant [signedBy <signer>,] [codeBase <code source>] {  
   permission  <class>  [<name> [, <action list>]];  
};  
```  
  
 下列程式碼基底應該限制為 JDBC 驅動程式程式碼基底，以確定您授與最少量的權限。  
  
```  
grant codeBase "file:/install_dir/lib/-" {  
  
// Grant access to data source.  
permission java.util.PropertyPermission "java.naming.*", "read,write";  
  
// Specify which hosts can be connected to.  
permission java.net.socketPermission "host:port", "connect";  
  
// Logger permission to take advantage of logging.  
permission java.util.logging.LoggingPermission;  
  
// Grant listen/connect/accept permissions to the driver if   
// connecting to a named instance as the client driver.   
// This connects to a udp service and listens for a response.  
permission java.net.SocketPermission "*", "listen, connect, accept";   
};   
```  
  
> [!NOTE]  
>  程式碼 "file:/install_dir/lib/-" 是指 JDBC 驅動程式的安裝目錄。  
  
## <a name="protecting-server-communication"></a>保護伺服器通訊  
 使用 JDBC 驅動程式與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫進行通訊時，您可以使用網際網路通訊協定安全性 (IPSEC) 或安全通訊端層 (SSL)，或同時使用兩者來保護通訊通道。  
  
 SSL 支援可以用於提供 IPSEC 之外的其他保護等級。 如需使用 SSL 的詳細資訊，請參閱[Using SSL Encryption](../../connect/jdbc/using-ssl-encryption.md)。  
  
## <a name="see-also"></a>另請參閱  
 [保護 JDBC Driver 應用程式](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
