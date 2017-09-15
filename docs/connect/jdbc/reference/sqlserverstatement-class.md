---
title: "SQLServerStatement 類別 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec24963c-8b51-4838-91e9-1fbfa2347451
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b10213cf711ba2900888e5bd722a71475c0c97de
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverstatement-class"></a>SQLServerStatement 類別
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  代表 JDBC 陳述式功能的基本實作。  
  
 **封裝：** com.microsoft.sqlserver.jdbc  
  
 **實作：** [ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
public class SQLServerStatement  
```  
  
## <a name="remarks"></a>備註  
 SQLServerStatement 類別也會提供針對 JDBC 備妥及可呼叫陳述式的基底類別實作方法的數字。 SQLServerStatement 類別的基本角色是執行 SQL 陳述式，並接著傳回更新計數和結果集傳回給使用者應用程式。  
  
 這個類別支援解除包裝成為 SQLServerStatement 類別、 ISQLServerStatement 介面和 java.sql.Statement 介面。 如需詳細資訊，請參閱[包裝函式和介面](../../../connect/jdbc/wrappers-and-interfaces.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerStatement 成員](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [JDBC 驅動程式 API 參考](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
