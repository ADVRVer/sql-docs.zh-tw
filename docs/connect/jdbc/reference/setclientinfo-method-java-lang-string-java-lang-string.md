---
title: setClientInfo 方法 (java.lang.String, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8d050831-8305-48a8-bd22-207932111040
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b94f6a00e26934426ef1ece760ce1179c3c53046
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "76941176"
---
# <a name="setclientinfo-method-javalangstring-javalangstring"></a>setClientInfo 方法 (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  設定指定之用戶端資訊屬性的值。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void setClientInfo (java.lang.String name,  
                           java.lang.String value)  
```  
  
#### <a name="parameters"></a>參數  
 *name*  
  
 String，包含要設定之用戶端資訊屬性的名稱。  
  
 *value*  
  
 String，包含要用來設定用戶端資訊屬性的值。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 此 setClientInfo 方法是由 java.sql.Connection 介面中的 setClientInfo 方法所指定。  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 不支援任何用戶端資訊屬性。 在 2.0 JDBC 驅動程式中，這個方法會針對屬性產生警告。 應用程式必須使用 [SQLServerConnection](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md) 類別的 [getWarnings](../../../connect/jdbc/reference/sqlserverconnection-class.md) 方法來擷取警告。  
  
## <a name="see-also"></a>另請參閱  
 [setClientInfo 方法 &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection 成員](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection 類別](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
