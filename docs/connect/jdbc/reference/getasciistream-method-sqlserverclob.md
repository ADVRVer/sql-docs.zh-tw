---
title: getAsciiStream 方法 (SQLServerClob) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.getAsciiStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 134abe5e-5add-4d27-b333-b4b0f4d94c31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2490fc903f7c1c509adc1e6f776f00a39e5f4616
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47767266"
---
# <a name="getasciistream-method-sqlserverclob"></a>getAsciiStream 方法 (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  具體化此 CLOB 當做 ASCII 資料流。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.io.InputStream getAsciiStream()  
```  
  
## <a name="return-value"></a>傳回值  
 包含 CLOB 資料的輸入資料流。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 getAsciiStream 方法是由 java.sql.Clob 介面中 getAsciiStream 方法指定。  
  
 一定會傳回位元組的資料流，並假設 CLOB 中的資料為 ASCII 格式，因為無法得知它是否為 Unicode 或是其他任何多位元組字碼頁。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerClob 方法](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob 成員](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob 類別](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
