---
title: "deleteRow 方法 (SQLServerResultSet) |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerResultSet.deleteRow
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: aa04a644-c7c2-4738-8b6e-7fea566d2c16
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8e6ee48f50f91e6c46099c5987df4c2f034398fe
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="deleterow-method-sqlserverresultset"></a>deleteRow 方法 (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  刪除目前的資料列從這個[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)物件以及從基礎資料庫。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void deleteRow()  
```  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 deleteRow 方法是由 java.sql.ResultSet 介面中的 deleteRow 方法指定。  
  
 當資料指標位於插入資料列時，這個方法將無法進行呼叫。  
  
 當使用索引鍵集資料指標時，這個方法會在結果集中留下一個漏洞。 您可以使用測試這個漏洞[rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md)方法。 結果集中的資料列數不會變更。  
  
## <a name="see-also"></a>請參閱＜  
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
