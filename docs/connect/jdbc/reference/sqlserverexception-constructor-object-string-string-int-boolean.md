---
title: SQLServerException 建構函式 （java.lang.Object，java.lang.String，java.lang.String，int，布林值） |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7e6e0ef2f83c8dc0641cbaed60e6333590fc9ca1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sqlserverexception-constructor-javalangobject-javalangstring-javalangstring-int-boolean"></a>SQLServerException 建構函式 （java.lang.Object，java.lang.String，java.lang.String，int，布林值）
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  初始化的新執行個體[SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)類別時指定**物件**、**字串**物件**字串**物件、 **int**，和**布林**。

## <a name="syntax"></a>語法  
  
```  

public SQLServerException(java.lang.Object obj,
            java.lang.String errText,
            java.lang.String errState,
            int errNum,
            boolean bStack)

            
```  
  
#### <a name="parameters"></a>參數  
 *obj*  
  
 IO 緩衝區產生例外狀況。

 *errText*  
  
 字串，包含錯誤文字。
  
 *sqlState*  
  
 包含 SQL 狀態的列舉物件。
 
 *errNum*  
  
 包含例外狀況的錯誤碼是 int。
 
 *bStack*  
  
 布林值，指出是否應產生堆疊追蹤。
  
## <a name="see-also"></a>另請參閱  
 [SQLServerException 建構函式](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException 成員](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException 類別](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
