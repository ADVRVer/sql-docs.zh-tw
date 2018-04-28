---
title: moveToInsertRow 方法 (SQLServerResultSet) |Microsoft 文件
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
ms.topic: article
apiname:
- SQLServerResultSet.moveToInsertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f3c54bfe-d5b7-4f6e-ae6c-3e8954e5b1c9
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1f39608188e9de998c5f431561cf1482f5d50b3f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="movetoinsertrow-method-sqlserverresultset"></a>moveToInsertRow 方法 (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  將資料指標移動到插入資料列。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void moveToInsertRow()  
```  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 moveToInsertRow 方法是由 java.sql.ResultSet 介面中的 moveToInsertRow 方法指定。  
  
 當資料指標位於插入資料列時，便會記住目前的資料指標位置。 插入資料列是一種特殊資料列，它會與可更新的結果集產生關聯。 它基本上是一個緩衝區，將新的資料列加入到結果集之前，可以呼叫 updater 方法在其中建構該資料列。  
  
 僅限 updater、 getter 和[insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md)資料指標位於插入資料列時，就可以呼叫方法。 指定的值，每次呼叫此方法時，並呼叫 insertRow 之前，必須是結果集中的所有資料行。 必須先呼叫 updater 方法，然後才可以在資料行值上呼叫 getter 方法。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
