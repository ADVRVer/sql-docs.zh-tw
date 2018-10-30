---
title: deleteRow 方法 (SQLServerResultSet) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.deleteRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: aa04a644-c7c2-4738-8b6e-7fea566d2c16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 466fa86609ba4f784e78ba9ac0fb5178d827645e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47784116"
---
# <a name="deleterow-method-sqlserverresultset"></a>deleteRow 方法 (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  從這個 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 物件和基礎資料庫中，刪除目前的資料列。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void deleteRow()  
```  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 deleteRow 方法是由 java.sql.ResultSet 介面中的 deleteRow 方法指定。  
  
 當資料指標位於插入資料列時，這個方法將無法進行呼叫。  
  
 當使用索引鍵集資料指標時，這個方法會在結果集中留下一個漏洞。 您可以使用 [rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md) 方法來測試這個漏洞。 結果集中的資料列數不會變更。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
