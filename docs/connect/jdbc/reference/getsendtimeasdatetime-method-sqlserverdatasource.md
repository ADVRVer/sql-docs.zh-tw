---
title: getSendTimeAsDatetime 方法 (SQLServerDataSource) |Microsoft 文件
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
ms.assetid: 02287122-5dc1-455d-987f-95fd9a69d503
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f6df7971a2f594f3ce66c4e8a8d7bdf1b92962c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="getsendtimeasdatetime-method-sqlserverdatasource"></a>getSendTimeAsDatetime 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  這個方法加入在[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]JDBC 驅動程式 3.0。  
  
 傳回設定**sendTimeAsDatetime**連接屬性。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## <a name="return-value"></a>傳回值  
 **true**如果會 java.sql.Time 值傳送至伺服器的[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **datetime**型別。 **false**如果會 java.sql.Time 值傳送至伺服器的[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]**時間**型別。  
  
## <a name="remarks"></a>備註  
 請參閱[設定連接屬性](../../../connect/jdbc/setting-the-connection-properties.md)如需有關**sendTimeAsDatetime**連接屬性。  
  
 [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)可讓您以程式設計方式設定**sendTimeAsDatetime**連接屬性。  
  
 如需詳細資訊，請參閱[如何設定 java.sql.Time 值傳送給伺服器](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
