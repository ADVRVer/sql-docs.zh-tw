---
title: "supportsCatalogsInIndexDefinitions 方法 |Microsoft 文件"
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
- SQLServerDatabaseMetaData.supportsCatalogsInIndexDefinitions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a19423a0-e7b6-4f5c-94be-80ddf3fa4717
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ecca907599881acfbd7cbdf861673db72d95cb21
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="supportscatalogsinindexdefinitions-method-sqlserverdatabasemetadata"></a>supportsCatalogsInIndexDefinitions 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取值，此值指出目錄名稱是否可以用於索引定義陳述式。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean supportsCatalogsInIndexDefinitions()  
```  
  
## <a name="return-value"></a>傳回值  
 **true**受支援。 否則為 **false**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 supportsCatalogsInIndexDefinitions 方法是由 java.sql.DatabaseMetaData 介面中 supportsCatalogsInIndexDefinitions 方法指定。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成員](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 類別](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

