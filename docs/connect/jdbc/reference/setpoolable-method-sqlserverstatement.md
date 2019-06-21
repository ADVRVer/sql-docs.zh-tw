---
title: setPoolable 方法 (SQLServerStatement) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f0f798c8-cafb-4acc-b85d-2e0059c91d92
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c63c526aed7bfae6027f3a9aa028bc2a2e20fbef
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "66799645"
---
# <a name="setpoolable-method-sqlserverstatement"></a>setPoolable 方法 (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  要求共用或不共用陳述式。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void setPoolable(boolean poolable) throws SQLException  
```  
  
#### <a name="parameters"></a>參數  
 *poolable*  
  
 如果為 **true**，則表示應該共用陳述式。 如果為 **false**，則表示不應該共用陳述式。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 *poolable* 參數中指定的值是陳述式集區實作提示，可指出應用程式是否想要共用陳述式。 陳述式集區管理員會決定它是否使用該提示。  
  
 陳述式的集區值會套用到驅動程式所實作的內部陳述式快取，以及應用程式伺服器和其他應用程式所實作的外部陳述式快取。  
  
 根據預設，不是它建立 SQLServerStatement 物件。 SQLServerPreparedStatement 和 SQLServerCallableStatement 物件則在建立時，將可以共用。  
  
 如果這個方法在關閉的陳述式上呼叫，則會擲回 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)。  
  
 [isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md) 傳回值，指出是否可共用該物件。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerStatement 成員](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 類別](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
