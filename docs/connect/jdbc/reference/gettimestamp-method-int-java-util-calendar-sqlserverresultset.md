---
title: getTimestamp 方法 （int，java.util.Calendar） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getTimestamp (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f2dd5688-7344-437a-8716-7024fb8e9c31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c6d4908025700c6dda9a5636991ba3f799e628e8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667407"
---
# <a name="gettimestamp-method-int-javautilcalendar-sqlserverresultset"></a>getTimestamp 方法 (int, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  使用 Java 程式語言，並透過指定的日曆物件，擷取這個 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 物件中目前資料列中所指定資料行索引的值來當作 java.sql.Timestamp 物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.sql.Timestamp getTimestamp(int columnIndex,  
                                       java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>參數  
 *columnIndex*  
  
 指出資料行索引的 **int**。  
  
 *cal*  
  
 月曆物件。  
  
## <a name="return-value"></a>傳回值  
 時間戳記物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 GetTimestamp 方法 java.sql.ResultSet 介面中所指定這個 getTimestamp 方法。  
  
 這個方法只會傳回 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] datetime 和 smalldatetime 資料行中的值。  
  
## <a name="see-also"></a>另請參閱  
 [getTimestamp 方法 &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/gettimestamp-method-sqlserverresultset.md)   
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
