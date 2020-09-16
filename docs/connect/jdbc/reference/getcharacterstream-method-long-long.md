---
description: getCharacterStream 方法 (long, long)
title: getCharacterStream 方法 (long, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d70f502f-f60f-436a-83e6-797a0ed71bf3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 104cd4516a21e7679d54aaf0d95b9aaabb9ec760
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436790"
---
# <a name="getcharacterstream-method-long-long"></a>getCharacterStream 方法 (long, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  根據指定的位置和長度，傳回 **Clob** 資料作為 Reader 物件或字元資料流。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                         long length)  
```  
  
#### <a name="parameters"></a>參數  
 *pos*  
  
 **long**，指出所要擷取部分值的第一個字元位移。  
  
 *length* (長度)  
  
 **long**，指出將擷取的部分值字元長度。  
  
## <a name="return-value"></a>傳回值  
 Reader 物件，包含 **Clob** 資料。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 getCharacterStream 方法是由 java.sql.Clob 介面中的 getCharacterStream 方法所指定。  
  
## <a name="see-also"></a>另請參閱  
 [getCharacterStream 方法 &#40;SQLServerClob&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverclob.md)   
 [SQLServerClob 方法](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob 成員](../../../connect/jdbc/reference/sqlserverclob-members.md)  
  
  
