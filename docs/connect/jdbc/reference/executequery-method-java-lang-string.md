---
title: executeQuery 方法 (java.lang.String) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeQuery (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 610205c2-6bcd-426c-ad6f-9682551efdec
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3f881493288c385cb490f9d04b22acce03e19f29
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802307"
---
# <a name="executequery-method-javalangstring"></a>executeQuery 方法 (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  執行指定的 SQL 陳述式，並傳回單一 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
public final java.sql.ResultSet executeQuery(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>參數  
 *sql*  
  
 包含 SQL 陳述式的**字串**。  
  
## <a name="return-value"></a>傳回值  
 SQLServerResultSet 物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 executeQuery 方法是由 java.sql.Statement 介面中的 executeQuery 方法指定。  
  
 這個方法會覆寫 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 類別中找到的 [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) 方法。  
  
 呼叫這個方法將會產生例外狀況，因為當建立 SQLServerPreparedStatement 物件時，已指定此物件的 SQL 陳述式。  
  
 如果指定的 SQL 陳述式產生單一 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 物件以外的任何項目，則會擲回 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [executeQuery 方法 &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement 成員](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement 類別](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
