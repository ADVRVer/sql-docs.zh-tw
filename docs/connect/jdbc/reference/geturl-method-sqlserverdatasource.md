---
title: "getURL 方法 (SQLServerDataSource) |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.getURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dd0d5d2c-91fe-4b0f-a162-69d898ba176e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d0ea89d9dab71fcc1572ad6113a76aa2f5face79
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="geturl-method-sqlserverdatasource"></a>getURL 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  傳回用來連接到資料來源的 URL。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.lang.String getURL()  
```  
  
## <a name="return-value"></a>傳回值  
 A**字串**包含 URL。  
  
## <a name="remarks"></a>備註  
 基於安全性理由，您不應該包含密碼提供給在 URL 中[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)方法。 原因是因為協力廠商 Java 應用程式伺服器會經常顯示其資料來源組態使用者介面中所設定的 URL 屬性值。 請改用[setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)方法來設定密碼值。 這樣一來，Java 應用程式伺服器將不會顯示其資料來源組態使用者介面中所設定的密碼。  
  
> [!NOTE]  
>  GetURL 如果 setURL 方法未呼叫 getURL 方法之前呼叫，傳回的預設值"sqlserver: / /"。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

