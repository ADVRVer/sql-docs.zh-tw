---
title: "position 方法 (java.lang.String，long) |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerClob.position (java.lang.String, long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 86fad8ed-375a-42e1-b40e-1fa085957a2c
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a4b196ecb4d9670fe0b2bcf24e6305e40d74b335
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="position-method-javalangstring-long"></a>position 方法 (java.lang.String, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  依據給定的開始位置，傳回 CLOB 內指定之子字串的字元位置。  
  
## <a name="syntax"></a>語法  
  
```  
  
public long position(java.lang.String searchstr,  
                     long start)  
```  
  
#### <a name="parameters"></a>參數  
 *searchstr*  
  
 要搜尋的子字串。  
  
 *啟動*  
  
 開始搜尋的位置，第一個位置是 1。  
  
## <a name="return-value"></a>傳回值  
 子字串的出現位置，如果未出現則為 -1。第一個位置是 1。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個位置的方法是由 java.sql.Clob 介面中的位置方法指定。  
  
## <a name="see-also"></a>另請參閱  
 [將方法 &#40;SQLServerClob &#41;](../../../connect/jdbc/reference/position-method-sqlserverclob.md)   
 [SQLServerClob 方法](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob 成員](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob 類別](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  

