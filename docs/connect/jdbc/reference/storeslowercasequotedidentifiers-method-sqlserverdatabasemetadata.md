---
title: "storesLowerCaseQuotedIdentifiers 方法 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDatabaseMetaData.storesLowerCaseQuotedIdentifiers
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 3e104c9e-66d4-436b-8b5b-a00ff667c95b
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8b2bb8ea6754293a1b31d2bb4f769a283506a5f9
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="storeslowercasequotedidentifiers-method-sqlserverdatabasemetadata"></a>storesLowerCaseQuotedIdentifiers 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取值，此值指出這個資料庫是否會依不區分大小寫的方式來處理已加上引號的混合大小寫字母之 SQL 識別碼，並將它們儲存成小寫字母。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean storesLowerCaseQuotedIdentifiers()  
```  
  
## <a name="return-value"></a>傳回值  
 **true**如果以小寫字母會儲存識別項。 否則為 **false**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 storesLowerCaseQuotedIdentifiers 方法是由 java.sql.DatabaseMetaData 介面中 storesLowerCaseQuotedIdentifiers 方法指定。  
  
## <a name="see-also"></a>請參閱＜  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成員](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 類別](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
