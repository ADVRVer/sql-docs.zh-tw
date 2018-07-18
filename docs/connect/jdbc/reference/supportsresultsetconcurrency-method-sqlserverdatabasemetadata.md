---
title: supportsResultSetConcurrency 方法 (SQLServerDatabaseMetaData) |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsResultSetConcurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8f7573b2-ac5c-4721-8a02-4b6cb60c74b2
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 87b9db3f492cdb0399396b35a15a665be1d6cc49
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32851325"
---
# <a name="supportsresultsetconcurrency-method-sqlserverdatabasemetadata"></a>supportsResultSetConcurrency 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取值，此值指出這個資料庫是否支援結合使用給定的並行類型與給定的結果集類型。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean supportsResultSetConcurrency(int type,  
                                            int concurrency)  
```  
  
#### <a name="parameters"></a>參數  
 *type*  
  
 **Int** ，指出結果集類型，可以是下列值的其中一個定義於 java.sql.ResultSet 或 SQLServerResultSet 中：  
  
## <a name="javasqlresultset-types"></a>java.sql.ResultSet 型別  
 TYPE_FORWARD_ONLY  
  
 TYPE_SCROLL_SENSITIVE  
  
 TYPE_SCROLL_INSENSITIVE  
  
## <a name="sqlserverresultset-types"></a>SQLServerResultSet 型別  
 TYPE_SS_SCROLL_STATIC  
  
 TYPE_SS_SCROLL_KEYSET  
  
 TYPE_SS_DIRECT_FORWARD_ONLY  
  
 TYPE_SS_SERVER_CURSOR_FORWARD_ONLY  
  
 TYPE_SS_SCROLL_DYNAMIC  
  
 *並行存取*  
  
 **Int** ，指出結果集並行層級，可以是下列值的其中一個定義於 java.sql.ResultSet 或 SQLServerResultSet 中：  
  
## <a name="javasqlresultset-types"></a>java.sql.ResultSet 型別  
 CONCUR_READ_ONLY  
  
 CONCUR_UPDATABLE  
  
## <a name="sqlserverresultset-types"></a>SQLServerResultSet 型別  
 CONCUR_SS_OPTIMISTIC_CC  
  
 CONCUR_SS_SCROLL_LOCKS  
  
 CONCUR_SS_OPTIMISTIC_VAL  
  
## <a name="return-value"></a>傳回值  
 **true**受支援。 否則為 **false**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 supportsResultSetConcurrency 方法是由 java.sql.DatabaseMetaData 介面中 supportsResultSetConcurrency 方法指定。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成員](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 類別](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
