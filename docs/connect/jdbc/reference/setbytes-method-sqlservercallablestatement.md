---
title: setBytes 方法 (SQLServerCallableStatement) |Microsoft 文件
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
apiname:
- SQLServerCallableStatement.setBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f264f1a6-ee35-4eaf-81d8-ecf99f03b35d
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 949f64c532fdbbca300028894ce4f7a822b6ae47
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="setbytes-method-sqlservercallablestatement"></a>setBytes 方法 (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定的參數設定為指定的陣列**位元組**值。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void setBytes(java.lang.String sCol,  
                     byte[] b)  
```  
  
#### <a name="parameters"></a>參數  
 *sCol*  
  
 A**字串**，其中包含參數名稱。  
  
 *B*  
  
 陣列**位元組**值。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 在舊版的驅動程式，您可以使用 SQLServerCallableStatement.setBytes 來轉換位元組陣列之間的值和[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]資料型別**日期**，**時間**， **datetime2**，或**datetimeoffset**。 現在，搭配這些資料類型使用這個方法將會引發例外狀況，指出不支援轉換。  
  
 SetBytes 方法 java.sql.CallableStatement 介面中所指定此 setBytes 方法。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerCallableStatement 成員](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement 類別](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
