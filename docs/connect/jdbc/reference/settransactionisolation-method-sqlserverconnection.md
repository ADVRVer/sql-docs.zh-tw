---
title: setTransactionIsolation 方法 (SQLServerConnection) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setTransactionIsolation
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6a8fa4d3-5237-40f8-8a02-b40a3d7a1131
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e7e803e60568030eb105fa52a15bc2c2bc4b3e8d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972288"
---
# <a name="settransactionisolation-method-sqlserverconnection"></a>setTransactionIsolation 方法 (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  嘗試將這個 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 物件的交易隔離等級變更為所指定等級。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void setTransactionIsolation(int level)  
```  
  
#### <a name="parameters"></a>參數  
 *level*  
  
 **int** 值，包含下列其中一個隔離等級：  
  
 TRANSACTION_READ_UNCOMMITTED  
  
 TRANSACTION_READ_COMMITTED  
  
 TRANSACTION_REPEATABLE_READ  
  
 TRANSACTION_SERIALIZABLE  
  
 TRANSACTION_SNAPSHOT = 0x1000  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 setTransactionIsolation 方法是由連接介面中的 setTransactionIsolation 方法指定。  
  
 如果在交易中間呼叫這個方法，便不會認可交易。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerConnection 成員](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection 類別](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
