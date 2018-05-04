---
title: executeUpdate 方法 （java.lang.String，java.lang.String） |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerStatement.executeUpdate (java.lang.String[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2f44a689-65c8-4c94-9574-e9c08ea7918e
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 08504da732634c16a6d2176f1430587046893ed1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="executeupdate-method-javalangstring-javalangstring"></a>executeUpdate 方法 （java.lang.String，java.lang.String）
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  執行給定的 SQL 陳述式並訊號[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]的自動產生索引鍵會指定在給定陣列中應該可供擷取。  
  
## <a name="syntax"></a>語法  
  
```  
  
public final int executeUpdate(java.lang.String sql,  
                               java.lang.String[] columnNames)  
```  
  
#### <a name="parameters"></a>參數  
 *sql*  
  
 A**字串**，其中包含 SQL 陳述式。  
  
 *columnNames*  
  
 類型的陣列**字串**指出的自動產生索引鍵資料行名稱可供使用。  
  
## <a name="return-value"></a>傳回值  
 **Int** ，指出資料列數目，0，是否影響使用 DDL 陳述式。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 executeUpdate 方法是由 java.sql.Statement 介面中的 executeUpdate 方法指定。  
  
 如果執行預存程序會導致更新計數大於一，或是產生多個結果集，使用[執行](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)方法才能執行預存程序。  
  
## <a name="see-also"></a>另請參閱  
 [executeUpdate 方法&#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [SQLServerStatement 成員](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 類別](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
