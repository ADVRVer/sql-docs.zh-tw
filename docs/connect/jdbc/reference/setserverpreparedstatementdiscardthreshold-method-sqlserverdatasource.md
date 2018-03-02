---
title: "setServerPreparedStatementDiscardThreshold 方法 (SQLServerDataSource) |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2018
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
ms.assetid: 
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5cbda72d00f8af453989e59f0591f519f872609c
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2018
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>setServerPreparedStatementDiscardThreshold 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  設定 serverPreparedStatementDiscardThreshold 連接屬性的值。 此設定會控制多少未完成備妥的陳述式捨棄之前呼叫，以清除伺服器上未處理的控制代碼將會執行動作 (sp_unprepare) 可以是未處理的每個連接。 當設定為 < = 1 unprepare 動作會立即關閉已備妥的陳述式上執行。 如果值設定為 > 1 以避免太過頻繁呼叫 sp_unprepare 的額外負荷一起批次處理這些呼叫
 
## <a name="syntax"></a>語法  
  
```
public void setServerPreparedStatementDiscardThreshold(int enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>參數  
 *serverPreparedStatementDiscardThreshold*  
  
 新值**serverPreparedStatementDiscardThreshold**連接屬性。  

## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>備註  
 這個方法是從 JDBC 驅動程式版本 6.4 可用且向外。
 
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
