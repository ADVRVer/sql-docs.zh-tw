---
title: "getFloat 方法 (int) |Microsoft 文件"
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
apiname: SQLServerCallableStatement.getFloat (int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 40178471-4f35-4df9-b3fb-80cdf43de274
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e29fc8307587cd82fc90aaaf7aa74c21fd8eda6c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="getfloat-method-int"></a>getFloat 方法 (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取所指定之參數的值**float**在 Java 程式語言中使用給定的參數索引。  
  
## <a name="syntax"></a>語法  
  
```  
  
public float getFloat(int index)  
```  
  
#### <a name="parameters"></a>參數  
 *索引*  
  
 **Int** ，指出參數索引。  
  
## <a name="return-value"></a>傳回值  
 A **float**值。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 GetFloat 方法 java.sql.CallableStatement 介面中所指定此 getFloat 方法。  
  
 這個方法會傳回所有數字為基礎的類型，使用 Java **float**精確度。  
  
## <a name="see-also"></a>請參閱＜  
 [getFloat 方法 &#40;SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getfloat-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 成員](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement 類別](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
