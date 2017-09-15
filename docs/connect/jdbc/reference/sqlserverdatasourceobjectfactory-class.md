---
title: "SQLServerDataSourceObjectFactory 類別 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 19f81b3a458ac0fa2d5e276858fcff45eeb0eb4b
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverdatasourceobjectfactory-class"></a>SQLServerDataSourceObjectFactory 類別
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  代表可具體化來自 Java Naming and Directory Interface (JNDI) 之資料來源的物件 Factory。  
  
 **封裝：** com.microsoft.sqlserver.jdbc  
  
 **擴充：** java.lang.Object  
  
 **實作：** javax.naming.spi.ObjectFactory  
  
## <a name="syntax"></a>語法  
  
```  
  
public class SQLServerDataSourceObjectFactory  
```  
  
## <a name="remarks"></a>備註  
 所有的資料來源類別都會繼承這個方法。 做為其對 Referenceable 介面的支援一部分[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]ObjectFactory 會實作這個類別會公開。 Java 應用程式伺服器會在資料來源類別上呼叫 getReference，這會建立參考物件在內部使用的類別名稱做為其 class factory。  
  
 在 Java 應用程式伺服器取值 （dereference） 參考物件時，它會建立 SQLServerDataSourceObjectFactory 物件和呼叫的執行個體[getObjectInstance](../../../connect/jdbc/reference/getobjectinstance-method-sqlserverdatasourceobjectfactory.md)方法，將在所參考的物件傳遞至擷取資料來源執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSourceObjectFactory 成員](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [JDBC 驅動程式 API 參考](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
