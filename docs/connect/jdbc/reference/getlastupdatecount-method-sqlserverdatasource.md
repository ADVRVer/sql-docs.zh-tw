---
title: "getLastUpdateCount 方法 (SQLServerDataSource) |Microsoft 文件"
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
apiname: SQLServerDataSource.getLastUpdateCount
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 4c4fbb24-0b02-42da-928c-a903bb591cc7
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: db133035f7145c61fb856fcfa308550d9883da17
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="getlastupdatecount-method-sqlserverdatasource"></a>getLastUpdateCount 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  傳回**布林**值，指出是否啟用 lastUpdateCount 屬性。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean getLastUpdateCount()  
```  
  
## <a name="return-value"></a>傳回值  
 **true**如果啟用 lastupdatecount 屬性。 否則為 **false**。  
  
## <a name="remarks"></a>備註  
 如果 lastUpdateCount 屬性設定為**true**、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]將傳回的最後一個更新計數的 SQL 陳述式傳遞至伺服器。 如果 lastUpdateCount 屬性設定為**false**，驅動程式會傳回所有更新計數，包括所傳回的任何可能已引發之觸發程序。 如果未設定 lastUpdateCount 屬性，getLastUpdateCount 方法會傳回預設值的**true**。  
  
## <a name="see-also"></a>請參閱＜  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
