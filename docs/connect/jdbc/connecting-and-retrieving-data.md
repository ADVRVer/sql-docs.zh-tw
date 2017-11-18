---
title: "連接及擷取資料 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 506a577f8a1623a31ccb0901b00a3376b72ef262
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-and-retrieving-data"></a>連接及擷取資料
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  當您正在使用[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]，有兩種主要的方法來建立連接[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]資料庫。 其中一個是在連接 URL 中，設定連接屬性，然後呼叫 getConnection 方法要傳回之 DriverManager 類別[SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)物件。  
  
> [!NOTE]  
>  如需 JDBC 驅動程式支援的連接屬性的清單，請參閱[設定連接屬性](../../connect/jdbc/setting-the-connection-properties.md)。  
  
 第二種方法牽涉到設定連接屬性所使用的 setter 方法[SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)類別，然後再呼叫[getConnection](../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)方法以傳回 SQLServerConnection物件。  
  
 本節中的主題描述您可以連接到不同的方式[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]資料庫，而且它們也示範擷取資料的不同技術。  
  
## <a name="in-this-section"></a>本節內容  
  
|主題|Description|  
|-----------|-----------------|  
|[連接 URL 範例](../../connect/jdbc/connection-url-sample.md)|描述如何使用連接 URL 連接到[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]然後使用 SQL 陳述式來擷取資料。|  
|[資料來源範例](../../connect/jdbc/data-source-sample.md)|說明如何使用資料來源來連接到 SQL Server，然後使用預存程序來擷取資料。|  
  
## <a name="see-also"></a>另請參閱  
 [範例 JDBC 驅動程式應用程式](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  

