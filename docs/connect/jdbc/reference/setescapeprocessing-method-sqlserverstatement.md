---
title: "setEscapeProcessing 方法 (SQLServerStatement) |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerStatement.setEscapeProcessing
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 6ac0682e-e04c-4fdb-893b-92408d42051e
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b3c59b96934734b23512039a5748df17c92a6ef8
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="setescapeprocessing-method-sqlserverstatement"></a>setEscapeProcessing 方法 (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  設定逸出處理模式。  
  
> [!NOTE]  
>  逸出處理[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]永遠為啟用狀態。 設定這個方法成 false 時不會有任何作用。  
  
## <a name="syntax"></a>語法  
  
```  
  
public final void setEscapeProcessing(boolean enable)  
```  
  
#### <a name="parameters"></a>參數  
 *啟用*  
  
 **true**啟用逸出處理。 否則為 **false**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 SetEscapeProcessing 方法 java.sql.Statement 介面中所指定此 setEscapeProcessing 方法。  
  
## <a name="see-also"></a>請參閱＜  
 [SQLServerStatement 成員](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 類別](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
