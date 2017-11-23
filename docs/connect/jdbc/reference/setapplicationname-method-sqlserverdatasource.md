---
title: "setApplicationName 方法 (SQLServerDataSource) |Microsoft 文件"
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
apiname: SQLServerDataSource.setApplicationName
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 24d6e48d-53c4-4da2-a6de-1cdff463c9cd
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6b7d9477ec7fd38d464decb22c943cdc62eb7975
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="setapplicationname-method-sqlserverdatasource"></a>setApplicationName 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  設定應用程式名稱。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void setApplicationName(java.lang.String applicationName)  
```  
  
#### <a name="parameters"></a>參數  
 *應用程式名稱*  
  
 A**字串**，其中包含應用程式的名稱。  
  
## <a name="remarks"></a>備註  
 應用程式名稱用來識別特定的應用程式中各種[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]分析和記錄工具。 如果未設定應用程式名稱，getApplicationName 方法會傳回未當地語系化的字串"[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]"。  
  
## <a name="see-also"></a>請參閱＜  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
