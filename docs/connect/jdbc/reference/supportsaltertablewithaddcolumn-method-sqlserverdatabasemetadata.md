---
description: supportsAlterTableWithAddColumn 方法 (SQLServerDatabaseMetaData)
title: supportsAlterTableWithAddColumn 方法 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsAlterTableWithAddColumn
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bbac1370-fbf6-4450-8599-4ed3b4db3fc6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f9ad0ed428e25e9568664e583f9ba29e323a10df
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458110"
---
# <a name="supportsaltertablewithaddcolumn-method-sqlserverdatabasemetadata"></a>supportsAlterTableWithAddColumn 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取值，此值指出這個資料庫是否支援使用加入資料行的 ALTER TABLE。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean supportsAlterTableWithAddColumn()  
```  
  
## <a name="return-value"></a>傳回值  
 如果支援，則為 **true**。 否則為 **false**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 supportsAlterTableWithAddColumn 方法是由 java.sql.DatabaseMetaData 介面中的 supportsAlterTableWithAddColumn 方法所指定。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成員](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 類別](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
