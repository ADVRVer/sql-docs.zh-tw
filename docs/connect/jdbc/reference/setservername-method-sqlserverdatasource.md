---
title: "setServerName 方法 (SQLServerDataSource) |Microsoft 文件"
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
apiname: SQLServerDataSource.setServerName
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 70920828-eda0-4064-be9f-c1e460db8f00
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2dcdf0aa279e1627cd6d2d60b96c92f88471076f
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="setservername-method-sqlserverdatasource"></a>setServerName 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  設定正在執行的電腦名稱[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void setServerName(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>參數  
 *伺服器名稱*  
  
 A**字串**包含伺服器名稱。  
  
## <a name="remarks"></a>備註  
 伺服器名稱是正在執行的目標電腦的主機名稱[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]。 如果未設定 serverName 屬性， [getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md)會傳回預設值是 null。  
  
## <a name="see-also"></a>請參閱＜  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
