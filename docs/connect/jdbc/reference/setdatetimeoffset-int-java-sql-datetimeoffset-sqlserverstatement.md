---
title: "setDateTimeOffset （int，java.sql.DateTimeOffset） |Microsoft 文件"
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
ms.assetid: e8b6e380-6b53-489b-be73-73fcb5258269
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b9b18af7823f8d02f80ba636fe57b5d6cd807770
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="setdatetimeoffsetint-javasqldatetimeoffset-sqlserverstatement"></a>setDateTimeOffset(int, java.sql.DateTimeOffset) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  將指定的參數設定為給定的 DateTimeOffset 值。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void setDateTimeOffset(int parameterIndex, DateTimeOffset dateTime)  
```  
  
#### <a name="parameters"></a>參數  
 *parameterIndex*  
  
 要設定之資料行的索引。  
  
 *dateTimeOffset*  
  
 DateTimeOffset 物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 DateTimeOffset 格式為 "YYYY-MM-DD HH-MM-SS[.nnnnnnn] [+][-] HH:MM"。 使用下表當做參考。  
  
|SQL 型別|Insert|  
|--------------|------------|  
|datetime|只能插入："YYYY-MM-DD hh:mm:ss[.nnn]"|  
|smalldatetime|只能插入："YYYY-MM-DD hh:mm:ss"|  
|Time|只能插入："hh:mm:ss[.nnnnnnn]"|  
|日期|只能插入："YYYY-MM-DD"|  
|datetime2|只能插入："YYYY-MM-DD hh:mm:ss[.nnnnnnn]"|  
  
## <a name="see-also"></a>請參閱＜  
 [getDateTimeOffset &#40;SQLServerResultSet &#41;](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [SQLServerStatement 成員](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 類別](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
