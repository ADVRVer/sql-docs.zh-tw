---
title: setServerPreparedStatementDiscardThreshold 方法 (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c47579114bab412a68698ef4c589ba32673328a7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47824006"
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>setServerPreparedStatementDiscardThreshold 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  設定 serverPreparedStatementDiscardThreshold 連接屬性的值。 此設定會控制多少未完成已備妥陳述式捨棄動作 (sp_unprepare) 可以是未處理的每個連接，呼叫以清除 在伺服器上未處理的控制代碼會在執行之前。 當此設定是 < = 1 unprepare 動作會立即關閉已備妥的陳述式上執行。 如果值設為 > 1 以避免太頻繁呼叫 sp_unprepare 的額外負荷一起批次處理這些呼叫
 
## <a name="syntax"></a>語法  
  
```
public void setServerPreparedStatementDiscardThreshold(int enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>參數  
 *serverPreparedStatementDiscardThreshold*  
  
 新值**serverPreparedStatementDiscardThreshold**連接屬性。  

## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 這個方法是從 JDBC 驅動程式版本 6.4 可用且向外。
 
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
