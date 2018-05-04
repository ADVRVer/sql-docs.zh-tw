---
title: getSubString 方法 (SQLServerClob) |Microsoft 文件
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
- SQLServerClob.getSubString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bf915590-a883-4403-befa-5b5bb42f34d8
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8feb8172c83f414b9a9cfd28b5f96a1b2a4ef1a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="getsubstring-method-sqlserverclob"></a>getSubString 方法 (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  依據給定開始位置以及要複製的字元數目，傳回 CLOB 中所指定之子字串的複本。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.lang.String getSubString(long pos,  
                                     int length)  
```  
  
#### <a name="parameters"></a>參數  
 *pos*  
  
 要從子字串中擷取的第一個字元。 第一個字元落在位置 1。  
  
 *長度*  
  
 要複製的連續字元數目。  
  
## <a name="return-value"></a>傳回值  
 A**字串**也就是指定的子字串 CLOB 中。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 getSubString 方法是由 java.sql.Clob 介面中 getSubString 方法指定。  
  
 嘗試從 null 或零長度 CLOB 中取得零個字元時，將會傳回空字串。 嘗試在零長度 CLOB 中的位置 1 以外之任何位置取得任何長度的字元時，將會擲回位置例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerClob 方法](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob 成員](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob 類別](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
