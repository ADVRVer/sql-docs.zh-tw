---
title: "getMaxColumnsInIndex 方法 (SQLServerDatabaseMetaData) |Microsoft 文件"
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
apiname: SQLServerDatabaseMetaData.getMaxColumnsInIndex
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 108f0e2c-7dc5-4195-8248-0758a75a314e
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f4804e6b7b7315a35d7e3938c8919627f783b2cc
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="getmaxcolumnsinindex-method-sqlserverdatabasemetadata"></a>getMaxColumnsInIndex 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取這個資料庫允許在索引中使用的最大資料行數目。  
  
## <a name="syntax"></a>語法  
  
```  
  
public int getMaxColumnsInIndex()  
```  
  
## <a name="return-value"></a>傳回值  
 **Int** ，指出允許的資料行數目上限。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 getMaxColumnsInIndex 方法是由 java.sql.DatabaseMetaData 介面中 getMaxColumnsInIndex 方法指定。  
  
## <a name="see-also"></a>請參閱＜  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成員](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 類別](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
