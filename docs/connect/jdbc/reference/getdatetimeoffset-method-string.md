---
title: getDateTimeOffset 方法 （字串） |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fedb1d75-0c3d-4eb3-ae65-da0e153265cc
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cb2a2fe886e0a71256bfae0f9677ad043a717d25
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="getdatetimeoffset-method-string"></a>getDateTimeOffset 方法 (String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  這個方法加入在[!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC 驅動程式 3.0。  
  
 擷取所指定之參數的值[DateTimeOffset 類別](../../../connect/jdbc/reference/datetimeoffset-class.md)Java 程式語言中使用給定的參數索引中的物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
public microsoft.sql.DateTimeOffset getDateTimeOffset(String sCol)  
```  
  
#### <a name="parameters"></a>參數  
 *sCol*  
  
 參數的名稱。  
  
## <a name="return-value"></a>傳回值  
 A [DateTimeOffset 類別](../../../connect/jdbc/reference/datetimeoffset-class.md)物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 您可以設定[DateTimeOffset 類別](../../../connect/jdbc/reference/datetimeoffset-class.md)參數值與[SQLServerCallableStatement.setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlservercallablestatement.md)。  
  
## <a name="see-also"></a>另請參閱  
 [getDateTimeOffset 方法&#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 成員](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement 類別](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
