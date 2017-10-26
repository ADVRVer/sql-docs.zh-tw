---
title: "setFetchDirection 方法 (SQLServerResultSet) |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerResultSet.setFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4ee82290-508d-4bff-a5c5-8a56338deef8
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dd6ab9a94acf883ed27cdd79fee886b6c54ca596
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="setfetchdirection-method-sqlserverresultset"></a>setFetchDirection 方法 (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  提供提示，當做方向中的資料列在這個[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)物件將會處理。  
  
> [!NOTE]  
>  這個方法目前不支援由[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]。 當您使用這個方法時，JDBC Driver 會記住設定，但是不會立刻執行。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void setFetchDirection(int direction)  
```  
  
#### <a name="parameters"></a>參數  
 *方向*  
  
 **Int** ，指出建議的提取方向。 可以是下列其中一個值：  
  
 ResultSet.FETCH_FORWARD  
  
 ResultSet.FETCH_REVERSE  
  
 ResultSet.FETCH_UNKNOWN  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 setFetchDirection 方法是由 java.sql.ResultSet 介面中的 setFetchDirection 方法所指定。  
  
 這個方法的起始值由[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)產生這個 SQLServerResultSet 物件的物件。 提取方向可以隨時變更。  
  
> [!NOTE]  
>  當資料指標類型為順向時，使用這個方法不會產生任何作用。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

