---
title: getBoolean 方法 (java.lang.String) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getBoolean (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c9ee851f-1827-42f5-a50a-bdef3e323a5e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 55174bc7e7a5b91910a9f76239cd0ed85ee78548
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "66771600"
---
# <a name="getboolean-method-javalangstring"></a>getBoolean 方法 (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  透過指定的參數名稱，擷取所指定參數的值來作為 **boolean** 值。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean getBoolean(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>參數  
 *sCol*  
  
 包含參數名稱的**字串**。  
  
## <a name="return-value"></a>傳回值  
 **boolean** 值。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 getBoolean方法是由 java.sql.CallableStatement 介面中的 getBoolean方法指定。  
  
## <a name="see-also"></a>另請參閱  
 [getBoolean 方法 &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getboolean-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 成員](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement 類別](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
