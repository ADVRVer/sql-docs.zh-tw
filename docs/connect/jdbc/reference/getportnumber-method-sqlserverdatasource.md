---
title: "getPortNumber 方法 (SQLServerDataSource) |Microsoft 文件"
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
apiname: SQLServerDataSource.getPortNumber
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: e5dc38d0-4340-4ad7-a56e-1d2a0f0fd846
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0ab9d426cea1048f7902af97c68951347c12e16d
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="getportnumber-method-sqlserverdatasource"></a>getPortNumber 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  傳回目前用來與通訊的通訊埠編號[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
  
public int getPortNumber()  
```  
  
## <a name="return-value"></a>傳回值  
 **Int**值，包含目前的連接埠號碼。  
  
## <a name="remarks"></a>備註  
 連接埠號碼是開啟的通訊端連接時，會使用 TCP/IP 通訊埠編號[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]。 如果未設定 portNumber 屬性，getPortNumber 方法會傳回預設值 1433。  
  
> [!NOTE]  
>  [SetPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)方法不會進行任何範圍檢查傳入的連接埠值。 您可以傳遞無效的如 99999，而不觸發錯誤編號。  
  
## <a name="see-also"></a>請參閱＜  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
