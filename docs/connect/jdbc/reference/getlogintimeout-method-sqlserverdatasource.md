---
title: getLoginTimeout 方法 (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 316f067c-9e08-456a-af19-b80b0bbd4a5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26a7c8e0cc876c8d13e9beb621354cead2f6296c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708576"
---
# <a name="getlogintimeout-method-sqlserverdatasource"></a>getLoginTimeout 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  傳回這個 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) 物件在嘗試建立連接時的等候秒數。  
  
## <a name="syntax"></a>語法  
  
```  
  
public int getLoginTimeout()  
```  
  
## <a name="return-value"></a>傳回值  
 **int** 值，代表要等候的秒數。  
  
## <a name="remarks"></a>Remarks  
 如果應用程式未明確指定逾時值，這個方法會傳回預設值 15 秒。  
  
 GetLoginTimeout 方法由 javax.sql.DataSource 介面中所指定這個 getLoginTimeout 方法。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
