---
title: SQLServerException 類別 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: af5ef257-7cf6-4db3-b1ee-07d22d82bef1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 40474f747022c34994dba9f34dbed15f1791c2af
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67971153"
---
# <a name="sqlserverexception-class"></a>SQLServerException 類別
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  代表 SQL 陳述式執行不成功或不完整。  
  
 **套件：** com.microsoft.sqlserver.jdbc  
  
 **擴充：** java.sql.SQLException  
  
 **實作：** java.io.Serializable  
  
## <a name="syntax"></a>語法  
  
```  
  
public final class SQLServerException  
```  
  
## <a name="remarks"></a>Remarks  
 SQLServerException 類別會同時處理 SQL 92 和 XOPEN 狀態碼。 這些狀態碼可以使用使用者指定的連接屬性來交換。 例外狀況會寫入任何已經指定的開啟記錄檔中。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerException 成員](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [JDBC 驅動程式 API 參考](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
