---
title: "cancel 方法 (SQLServerStatement) |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerStatement.cancel
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 276bd9c1-9329-4fc9-9622-ed673c83a12d
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b906ee23d28e42ff105d5d9bb919453193d90f68
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="cancel-method-sqlserverstatement"></a>cancel 方法 (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  取消目前正由此執行的 SQL 陳述式[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
public final void cancel()  
```  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個取消方法 cancel 方法 java.sql.Statement 介面中所指定。  
  
 當執行會產生單一大型順向、唯讀結果集的陳述式時，您可能只會對所傳回結果集中的部分開頭資料列集有興趣。 在此情況下，應用程式可能會呼叫[取消](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)相關的陳述式物件，再關閉該結果的方法設定以捨棄剩餘不必要的資料列所需的處理時間降至最低。 我們建議您在決定是否使用這項技巧時，權衡取捨可以節省的處理時間，以及伺服器在取消該執行時所需要的時間和額外往返。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerStatement 成員](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 類別](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

