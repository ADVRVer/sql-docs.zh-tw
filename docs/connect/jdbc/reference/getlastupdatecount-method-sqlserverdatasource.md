---
title: getLastUpdateCount 方法 (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getLastUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4c4fbb24-0b02-42da-928c-a903bb591cc7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b3e15720ad49cd90af30235a7c7a7d92ca104c78
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47733326"
---
# <a name="getlastupdatecount-method-sqlserverdatasource"></a>getLastUpdateCount 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  傳回 **Boolean** 值，這個值會指出是否啟用 lastUpdateCount 屬性。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean getLastUpdateCount()  
```  
  
## <a name="return-value"></a>傳回值  
 如果啟用 lastUpdateCount 屬性，則為 **true**； 否則為 **false**。  
  
## <a name="remarks"></a>Remarks  
 如果 lastUpdateCount 屬性設定為 **true**，[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 就只會從傳遞至伺服器的 SQL 陳述式傳回上次更新計數。 如果 lastUpdateCount 屬性設定為 **false**，此驅動程式將傳回所有更新計數，包括任何可能已引發之觸發程序所傳回的更新計數。 如果未設定 lastUpdateCount 屬性，getLastUpdateCount 方法會傳回預設值 **true**。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
