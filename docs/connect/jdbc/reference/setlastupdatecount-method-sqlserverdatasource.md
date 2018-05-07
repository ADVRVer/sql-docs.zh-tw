---
title: setLastUpdateCount 方法 (SQLServerDataSource) |Microsoft 文件
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
- SQLServerDataSource.setLastUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5487631a-1107-4169-84ca-b77fd09bea66
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0df8131bc286a4ffbc0fefb6f5dcb54f8447c26f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="setlastupdatecount-method-sqlserverdatasource"></a>setLastUpdateCount 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  設定**布林**值，指出是否啟用 lastUpdateCount 屬性。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void setLastUpdateCount(boolean lastUpdateCount)  
```  
  
#### <a name="parameters"></a>參數  
 *lastUpdateCount*  
  
 **true**如果啟用 lastupdatecount 屬性。 否則為 **false**。  
  
## <a name="remarks"></a>備註  
 如果 lastUpdateCount 屬性設定為**true**，[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]將傳回的最後一個更新計數的 SQL 陳述式傳遞至伺服器。 如果 lastUpdateCount 屬性設定為**false**，驅動程式會傳回所有更新計數，包括所傳回的任何可能已引發之觸發程序。 如果未設定 lastUpdateCount 屬性， [getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md)方法會傳回預設值**true**。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
