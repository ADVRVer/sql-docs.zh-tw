---
title: updateObject 方法 （java.lang.String，java.lang.Object） |Microsoft 文件
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
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateObject (java.lang.String, java.lang.Object)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f6999d9c-eab6-4e4d-96d8-e0fa4b4b87e3
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2cfb250d9cb00216f712f64407d607ad120b5188
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="updateobject-method-javalangstring-javalangobject"></a>updateObject 方法 (java.lang.String, java.lang.Object)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  更新指定的資料行與**物件**給定的資料行名稱的值。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void updateObject(java.lang.String columnName,  
                         java.lang.Object x)  
```  
  
#### <a name="parameters"></a>參數  
 *columnName*  
  
 A**字串**，其中包含資料行名稱。  
  
 *obj*  
  
 **物件**值。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 UpdateObject 方法 java.sql.ResultSet 介面中所指定此 updateObject 方法。  
  
## <a name="see-also"></a>另請參閱  
 [updateObject 方法&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateobject-method-sqlserverresultset.md)   
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
