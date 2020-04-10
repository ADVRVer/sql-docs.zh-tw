---
title: setDateTimeOffset(int, java.sql.DateTimeOffset) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e8b6e380-6b53-489b-be73-73fcb5258269
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a45711b4f3007f0f3c91f271542784386db99379
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927539"
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
  
|SQL 型別|插入|  
|--------------|------------|  
|Datetime|只能插入："YYYY-MM-DD hh:mm:ss[.nnn]"|  
|smalldatetime|只能插入："YYYY-MM-DD hh:mm:ss"|  
|Time|只能插入："hh:mm:ss[.nnnnnnn]"|  
|Date|只能插入："YYYY-MM-DD"|  
|DateTime2|只能插入："YYYY-MM-DD hh:mm:ss[.nnnnnnn]"|  
  
## <a name="see-also"></a>另請參閱  
 [getDateTimeOffset &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [SQLServerStatement 成員](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 類別](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
