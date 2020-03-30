---
title: isBeforeFirst 方法 (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.isBeforeFirst
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e0e2bd28-6949-47dc-b9dd-145ffb337069
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ffe17993b3a03563ec20e8f509e6eae2f6ed47cb
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "67977796"
---
# <a name="isbeforefirst-method-sqlserverresultset"></a>isBeforeFirst 方法 (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取值，此值指出資料指標是否出現在這個 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 物件的第一個資料列前面。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean isBeforeFirst()  
```  
  
## <a name="return-value"></a>傳回值  
 如果資料指標在第一個資料列之前，則為 **true**。 如果資料指標位於其他任何位置或者結果集未包含任何資料列，則為 **false**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 isBeforeFirst 方法是由 java.sql.ResultSet 介面中的 isBeforeFirst 方法所指定。  
  
 如果搭配動態資料指標使用這個方法，包括順向的唯讀資料指標，而且 selectMethod 連接屬性設定為 "cursor"，則會發生例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
