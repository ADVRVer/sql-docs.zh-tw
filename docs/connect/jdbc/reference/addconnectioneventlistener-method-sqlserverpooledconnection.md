---
title: addConnectionEventListener 方法 (SQLServerPooledConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPooledConnection.addConnectionEventListener
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 142830a8-8d4e-48ca-911d-85bf195ca4fe
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e1377e29329f43b9ea982f168e394537295ec889
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2020
ms.locfileid: "67955968"
---
# <a name="addconnectioneventlistener-method-sqlserverpooledconnection"></a>addConnectionEventListener 方法 (SQLServerPooledConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  註冊指定的事件接聽程式，如此一來，當這個 [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md) 物件上發生事件時，它就可以收到通知。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void addConnectionEventListener(javax.sql.ConnectionEventListener listener)  
```  
  
#### <a name="parameters"></a>參數  
 *listener*  
  
 ConnectionEventListener 物件。  
  
## <a name="remarks"></a>備註  
 這個 addConnectionEventListener 方法是由 javax.sql.PooledConnection 介面中的 addConnectionEventListener 方法所指定。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerPooledConnection 方法](../../../connect/jdbc/reference/sqlserverpooledconnection-methods.md)   
 [SQLServerPooledConnection 成員](../../../connect/jdbc/reference/sqlserverpooledconnection-members.md)   
 [SQLServerPooledConnection 類別](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
  
