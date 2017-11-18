---
title: "setBinaryStream 方法 （int，java.io.InputStream，int） |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerPreparedStatement.setBinaryStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fd6be063-08eb-40cf-9201-5a9f62387726
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d005664d5a193bf164c801eaaa043586ec9c2934
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="setbinarystream-method-int-javaioinputstream-int"></a>setBinaryStream 方法 (int, java.io.InputStream, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  將指定的參數設定為指定的輸入資料流，其中將包含指定的位元組數目。  
  
## <a name="syntax"></a>語法  
  
```  
  
public final void setBinaryStream(int n,  
                                  java.io.InputStream x,  
                                  int length)  
```  
  
#### <a name="parameters"></a>參數  
 *n*  
  
 **Int** ，指出參數編號。  
  
 *x*  
  
 InputStream 物件。  
  
 *length*  
  
 **Int** ，指出位元組數目。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 setBinaryStream 方法 setBinaryStream 方法 java.sql.PreparedStatement 介面中所指定。  
  
 如果資料流的長度就是從以指定的內容不同*長度*參數，JDBC 驅動程式會擲回例外狀況時更新或插入資料列。  
  
 如果資料流長度未知，*長度*參數可能會設定為-1，指出驅動程式應該接受資料流，無論其長度為何。 針對 sqljdbc4.jar，我們建議您使用 JDBC 4.0 方法[setBinaryStream 方法 &#40; int，java.io.InputStream &#41;](../../../connect/jdbc/reference/setbinarystream-method-int-java-io-inputstream.md)應用程式要從長度未知的資料流的資料行的更新。  
  
## <a name="see-also"></a>另請參閱  
 [setBinaryStream 方法 &#40;SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/setbinarystream-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement 成員](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  

