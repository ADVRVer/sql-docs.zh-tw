---
title: SQLServerException 建構函式 (java.lang.String、java.lang.String、int、java.lang.Throwable) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c8c90b5fcf9fd58bf4c6468603a91242fa1f935c
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80902554"
---
# <a name="sqlserverexception-constructor-javalangstring-javalangstring-int-javalangthrowable"></a>SQLServerException 建構函式 (java.lang.String、java.lang.String、int、java.lang.Throwable)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  當提供 [string](../../../connect/jdbc/reference/sqlserverexception-class.md) 物件、**string** 物件、**int**，以及 **throwable** 物件時，初始化 **SQLServerException** 類別的新執行個體。

## <a name="syntax"></a>語法  
  
```  
public SQLServerException(java.lang.String errText,
            SQLState errState,
            int errNum,
            java.lang.Throwable cause)
            
```  
  
#### <a name="parameters"></a>參數  
 *errText*  
  
 包含錯誤文字的字串。
  
 *errState*  
  
 包含錯誤狀態的字串。
 
 *errNum*  
  
 包含例外狀況之錯誤碼的 int。
 
 *cause*  
  
 包含例外狀況原因的 throwable 物件。
  
## <a name="see-also"></a>另請參閱  
 [SQLServerException 建構函式](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException 成員](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException 類別](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
