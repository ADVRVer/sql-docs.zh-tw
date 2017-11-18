---
title: "recover 方法 (SQLServerXAResource) |Microsoft 文件"
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
apiname:
- SQLServerXAResource.recover
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 840ecfcf-0dd3-4b7b-976f-dc9a96cd1464
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 07f102ffb57051bfd55638a18e8eff2a80025057
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="recover-method-sqlserverxaresource"></a>recover 方法 (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  從資源管理員取得備妥的交易分支清單。  
  
## <a name="syntax"></a>語法  
  
```  
  
public javax.transaction.xa.Xid[] recover(int flags)  
```  
  
#### <a name="parameters"></a>參數  
 *旗標*  
  
 **Int**可以採用下列值的其中一個值： XAResource.TMSTARTRSCAN 或 XAResource.TMENDRSCAN 或 XAResource.TMNOFLAGS 或 XAResource.TMSTARTTRSCAN |XAResource.TMENDRSCAN。  
  
## <a name="return-value"></a>傳回值  
 Xid 物件。  
  
## <a name="exceptions"></a>例外狀況  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>備註  
 此復原的方法是由 javax.transaction.xa.XAResource 介面中的復原方法指定。  
  
 如果參數**旗標**不 XAResource.TMSTARTRSCAN |XAResource.TMENDRSCAN，則表示復原掃描必須正在進行中。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerXAResource 方法](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource 成員](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource 類別](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  

