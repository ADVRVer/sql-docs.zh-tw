---
title: "addConnectionEventListener 方法 (SQLServerPooledConnection) |Microsoft 文件"
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
apiname: SQLServerPooledConnection.addConnectionEventListener
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 142830a8-8d4e-48ca-911d-85bf195ca4fe
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e61412a763568c6daced9efb22c72c11d85f3f37
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="addconnectioneventlistener-method-sqlserverpooledconnection"></a>addConnectionEventListener 方法 (SQLServerPooledConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  註冊指定的事件接聽程式，如此，這在發生事件時將會通知[SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void addConnectionEventListener(javax.sql.ConnectionEventListener listener)  
```  
  
#### <a name="parameters"></a>參數  
 *接聽程式*  
  
 ConnectionEventListener 物件。  
  
## <a name="remarks"></a>備註  
 這個 addConnectionEventListener 方法是由 javax.sql.PooledConnection 介面中 addConnectionEventListener 方法指定。  
  
## <a name="see-also"></a>請參閱＜  
 [SQLServerPooledConnection 方法](../../../connect/jdbc/reference/sqlserverpooledconnection-methods.md)   
 [SQLServerPooledConnection 成員](../../../connect/jdbc/reference/sqlserverpooledconnection-members.md)   
 [SQLServerPooledConnection 類別](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
  
