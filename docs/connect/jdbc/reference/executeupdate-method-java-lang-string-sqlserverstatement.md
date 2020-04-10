---
title: executeUpdate 方法 (java.lang.String) (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.executeUpdate (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 85e7c3a2-f2da-49bf-9d90-5fd246fd60e1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6432cd0d09dac50857a0bd1da16a3ded92bb09c5
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924258"
---
# <a name="executeupdate-method-javalangstring-sqlserverstatement"></a>executeUpdate 方法 (java.lang.String) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  執行可能是 INSERT、UPDATE 或 DELETE 陳述式的給定 SQL 陳述式，否則會是不傳回任何項目的 SQL 陳述式，例如 SQL DDL 陳述式。 從 [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 開始，executeUpdate 將會傳回 MERGE 作業中更新的正確資料列數目。  
  
## <a name="syntax"></a>語法  
  
```  
  
public int executeUpdate(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>參數  
 *sql*  
  
 包含 SQL 陳述式的 **String**。  
  
## <a name="return-value"></a>傳回值  
 **int** 會指出受影響的資料列數目，如果是使用 DDL 陳述式，則為 0。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 executeUpdate 方法是由 java.sql.Statement interface 介面中的 executeUpdate 方法指定。  
  
 如果執行預存程序產生的更新計數大於一或是產生一個以上的結果集，請使用 [execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) 方法執行預存程序。  
  
## <a name="see-also"></a>另請參閱  
 [executeUpdate 方法 &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [SQLServerStatement 成員](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 類別](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
