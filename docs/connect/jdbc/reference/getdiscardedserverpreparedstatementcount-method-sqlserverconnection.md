---
title: getDiscardedServerPreparedStatementCount 方法 (SQLServerConnection) |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.getDiscardedServerPreparedStatementCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9e5364a5569f555713eae94ddb46fb7439fed3f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32834603"
---
# <a name="getdiscardedserverpreparedstatementcount-method-sqlserverconnection"></a>getDiscardedServerPreparedStatementCount 方法 (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 傳回的目前未完成已備妥陳述式取消準備動作。

## <a name="syntax"></a>語法  
  
```  
  
public int getDiscardedServerPreparedStatementCount()  
```  

## <a name="return-value"></a>傳回值
 **Int** ，其中包含目前未完成的備妥陳述式的數字 unprepare 動作。

## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>備註  
 這個方法是從 JDBC 驅動程式版本 6.4 可用且向外。
 
## <a name="see-also"></a>另請參閱  
 [SQLServerConnection 成員](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection 類別](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
