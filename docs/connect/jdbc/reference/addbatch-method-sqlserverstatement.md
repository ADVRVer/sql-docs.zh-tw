---
title: addBatch 方法 (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.addBatch
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 95924a8b-a43c-4133-aff6-1d712e60e234
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c19e8cd92f7ee7aafcf6dd23e9c179f2557e628f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2020
ms.locfileid: "67955993"
---
# <a name="addbatch-method-sqlserverstatement"></a>addBatch 方法 (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  將所指定 SQL 命令新增至這個 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 物件的目前命令清單中。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void addBatch(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>參數  
 *sql*  
  
 包含 SQL 陳述式的**字串**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 addBatch 方法是由 java.sql.Statement 介面中的 addBatch 方法所指定。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerStatement 成員](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 類別](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
