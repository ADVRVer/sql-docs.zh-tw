---
description: setFetchSize 方法 (SQLServerResultSet)
title: setFetchSize 方法 (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.setFetchSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 233bf4f8-4758-42d0-a80b-33e34fa78027
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d984004b4d306462e2c1345344ebc8072f775a82
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431860"
---
# <a name="setfetchsize-method-sqlserverresultset"></a>setFetchSize 方法 (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  提供提示給 JDBC Driver，作為當這個 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 物件需要多個資料列時應從資料庫中提取的資料列數目。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void setFetchSize(int rows)  
```  
  
#### <a name="parameters"></a>參數  
 *rows*  
  
 指出要提取資料列數目的 **int**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 setFetchSize 方法是由 java.sql.ResultSet 介面中的 setFetchSize 方法指定。  
  
 如果指定的提取大小為零，則 JDBC 驅動程式會忽略此值，並預估應有的提取大小。 預設值由建立結果集的 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 物件設定。 提取大小可以隨時變更。  
  
 這個方法會變更伺服器資料指標的區塊提取大小，並在下一次 JDBC 驅動程式需要呼叫 sp_cursorfetch 時生效。 將提取大小設定為零會還原目前使用中之資料指標類型的預設提取大小。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
