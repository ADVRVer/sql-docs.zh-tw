---
title: setClientInfo 方法 （java.lang.String，java.lang.String） |Microsoft 文件
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
ms.topic: article
ms.assetid: 8d050831-8305-48a8-bd22-207932111040
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 42cb5ed2bef213c9c57f4aa71309a1afeb54b0eb
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="setclientinfo-method-javalangstring-javalangstring"></a>setClientInfo 方法 (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  設定指定之用戶端資訊屬性的值。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void setClientInfo (java.lang.String name,  
                           java.lang.String value)  
```  
  
#### <a name="parameters"></a>參數  
 *name*  
  
 字串，包含要設定的用戶端資訊屬性的名稱。  
  
 *value*  
  
 字串，包含要設定為用戶端資訊屬性的值。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 SetClientInfo 方法 java.sql.Connection 介面中所指定此 setClientInfo 方法。  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]不支援任何用戶端資訊屬性。 在 2.0 JDBC 驅動程式中，這個方法會針對屬性產生警告。 應用程式應該使用[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md)方法[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)類別來擷取警告。  
  
## <a name="see-also"></a>另請參閱  
 [setClientInfo 方法&#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection 成員](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection 類別](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
