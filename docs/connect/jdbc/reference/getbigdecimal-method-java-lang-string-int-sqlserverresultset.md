---
title: getBigDecimal 方法 (java.lang.String, int) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBigDecimal (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 572a1799-c232-400f-b8d8-37a5719a8d5e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 701afddaeaad79356a6b76a05a02f5cff1df1f39
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953907"
---
# <a name="getbigdecimal-method-javalangstring-int-sqlserverresultset"></a>getBigDecimal 方法 (java.lang.String, int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  使用指定的小數位數，擷取這個 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 物件之目前資料列中所指定資料行名稱的值。  
  
> [!NOTE]  
>  這個方法在 JDBC 規格中已被取代。 您應該改用 [getBigDecimal (java.lang.String)](../../../connect/jdbc/reference/getbigdecimal-method-java-lang-string-sqlserverresultset.md) 方法。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.math.BigDecimal getBigDecimal(java.lang.String columnName,  
                                          int scale)  
```  
  
#### <a name="parameters"></a>參數  
 *columnName*  
  
 包含資料行名稱的**字串**。  
  
 *scale*  
  
 **int**，指出小數點右邊的位數。  
  
## <a name="return-value"></a>傳回值  
 JAVA.math.bigdecimal 物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 getBigDecimal 方法是由 sql-dmo 介面中的 getBigDecimal 方法指定。  
  
## <a name="see-also"></a>另請參閱  
 [getBigDecimal 方法 &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getbigdecimal-method-sqlserverresultset.md)   
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
