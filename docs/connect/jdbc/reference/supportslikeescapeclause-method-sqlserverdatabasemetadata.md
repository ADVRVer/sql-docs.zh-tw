---
title: supportsLikeEscapeClause 方法 (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsLikeEscapeClause
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cfb43430-88bf-4386-847a-10ea1e5ce7db
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f2c062f1bf2235441be182d29af6bd3e83717fc1
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80912942"
---
# <a name="supportslikeescapeclause-method-sqlserverdatabasemetadata"></a>supportsLikeEscapeClause 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取值，此值指出這個資料庫是否支援指定 LIKE 逸出子句。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean supportsLikeEscapeClause()  
```  
  
## <a name="return-value"></a>傳回值  
 如果支援，則為 **true**。 否則為 **false**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 supportsLikeEscapeClause 方法是由 java.sql.DatabaseMetaData 介面中的 supportsLikeEscapeClause 方法指定。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成員](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 類別](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
