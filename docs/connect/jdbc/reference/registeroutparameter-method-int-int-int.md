---
title: registerOutParameter 方法 （int，int，int） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter (int, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d902d4e0-881f-4182-814c-0ede9a8da7fd
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: df9265a677d9e44c2d8834d3c45525b7af80142a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802110"
---
# <a name="registeroutparameter-method-int-int-int"></a>registerOutParameter 方法 (int, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  在給定 JDBC 型別和小數位數的指定序數位置中註冊 OUT 參數。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void registerOutParameter(int index,  
                                 int sqlType,  
                                 int scale)  
```  
  
#### <a name="parameters"></a>參數  
 *index*  
  
 **int**，指出參數的序數位置。  
  
 *sqlType*  
  
 JDBC 型別程式碼，如 java.sql.Types 中所定義。  
  
 *scale*  
  
 **int**，指出位於小數點右邊的位數。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 registerOutParameter 方法是由 java.sql.CallableStatement 介面中的 registerOutParameter 方法指定。  
  
 開頭[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]JDBC 驅動程式 3.0 中，當*sqlType*為的型別為 java.sql.Types.TIME，這個方法的行為由修改**sendTimeAsDatetime**連接屬性 ([設定連接屬性](../../../connect/jdbc/setting-the-connection-properties.md)) 和[SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)。  
  
 如需詳細資訊，請參閱 <<c0> [ 如何設定 java.sql.Time 值傳送給伺服器](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [registerOutParameter 方法 &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 成員](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement 類別](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
