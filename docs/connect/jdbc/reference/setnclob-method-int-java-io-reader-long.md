---
description: setNClob 方法 (int, java.io.Reader, long)
title: setNClob 方法 (int, java.io.Reader, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 11071f8f-0e9b-45f0-b600-aaef7e2815d8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e8c2a96bd9d2d114ce148e51f0728e9409cb4915
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431610"
---
# <a name="setnclob-method-int-javaioreader-long"></a>setNClob 方法 (int, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  將指定的參數設定為所指定 Reader 物件，該物件長度為指定的字元數。  
  
## <a name="syntax"></a>語法  
  
```  
  
public final void setNClob(int parameterIndex,  
                    java.io.Reader reader,  
                    long length)  
```  
  
#### <a name="parameters"></a>參數  
 *parameterIndex*  
  
 指出參數索引的 **int**。  
  
 *reader*  
  
 Reader 物件，指出參數值。  
  
 *length* (長度)  
  
 **long**，指出參數值中的字元數。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 setNClob 方法是由 java.sql.PreparedStatement 介面中的 setNClob 方法指定。  
  
## <a name="see-also"></a>另請參閱  
 [setNClob 方法 &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement 成員](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
