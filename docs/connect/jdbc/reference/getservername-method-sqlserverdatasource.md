---
title: "getServerName 方法 (SQLServerDataSource) |Microsoft 文件"
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
apiname: SQLServerDataSource.getServerName
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 3004ed22-5d69-4dd0-8761-d39f0b7dde13
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2302fded14543647060ce8ddcff4b59e0911c942
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="getservername-method-sqlserverdatasource"></a>getServerName 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  傳回名稱[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.lang.String getServerName()  
```  
  
## <a name="return-value"></a>傳回值  
 A**字串**如果未不設定任何值包含伺服器名稱或 null。  
  
## <a name="remarks"></a>備註  
 伺服器名稱是正在執行的目標電腦的主機名稱[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]。 如果未設定 getServerName 屬性，getservername 會傳回預設值是 null。  
  
## <a name="see-also"></a>請參閱＜  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
