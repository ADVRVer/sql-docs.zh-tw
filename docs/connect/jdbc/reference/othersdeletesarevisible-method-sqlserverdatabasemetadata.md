---
title: othersDeletesAreVisible 方法 (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.othersDeletesAreVisible
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c4692a8c-e6b7-4edc-9dad-7af816988de5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 710d06a43aa1eb23ae9750c1cee1b5c4d1460085
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "67976627"
---
# <a name="othersdeletesarevisible-method-sqlserverdatabasemetadata"></a>othersDeletesAreVisible 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取值，此值指出是否可看見其他人所做的刪除。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean othersDeletesAreVisible(int type)  
```  
  
#### <a name="parameters"></a>參數  
 *type*  
  
 指出結果集類型的 **int**，可以是定義於 java.sql.ResultSet 或 SQLServerResultSet 中的下列其中一個值：  
  
## <a name="javasqlresultset-types"></a>java.sql.ResultSet 型別  
 TYPE_FORWARD_ONLY  
  
 TYPE_SCROLL_SENSITIVE  
  
 TYPE_SCROLL_INSENSITIVE  
  
## <a name="sqlserverresultset-types"></a>SQLServerResultSet 型別  
 TYPE_SS_SCROLL_STATIC  
  
 TYPE_SS_SCROLL_KEYSET  
  
 TYPE_SS_DIRECT_FORWARD_ONLY  
  
 TYPE_SS_SERVER_CURSOR_FORWARD_ONLY  
  
 TYPE_SS_SCROLL_DYNAMIC  
  
## <a name="return-value"></a>傳回值  
 如果可以看見刪除，則為 **true**； 否則為 **false**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 othersDeletesAreVisible 方法是由 java.sql.DatabaseMetaData 介面中的 othersDeletesAreVisible 方法指定。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成員](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 類別](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
