---
title: "getFloat 方法 (int) (SQLServerResultSet) |Microsoft 文件"
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
apiname: SQLServerResultSet.getFloat (int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 30863ef5-7a7c-440e-8fbb-426a99266ee1
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 62895f0ed20bc1df5a610a12f07d30534cdf33bf
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="getfloat-method-int-sqlserverresultset"></a>getFloat 方法 (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取值，這個目前的資料列內指定之資料行索引的[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)物件當做**float**在 Java 程式語言。  
  
## <a name="syntax"></a>語法  
  
```  
  
public float getFloat(int columnIndex)  
```  
  
#### <a name="parameters"></a>參數  
 *columnIndex*  
  
 **Int** ，指出資料行索引。  
  
## <a name="return-value"></a>傳回值  
 A **float**值。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 GetFloat 方法 java.sql.ResultSet 介面中所指定此 getFloat 方法。  
  
 這個方法會傳回所有數字為基礎的類型，使用 Java **float**精確度。  
  
## <a name="see-also"></a>請參閱＜  
 [getFloat 方法 &#40;SQLServerResultSet &#41;](../../../connect/jdbc/reference/getfloat-method-sqlserverresultset.md)   
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
