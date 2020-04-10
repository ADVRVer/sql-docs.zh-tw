---
title: setResponseBuffering 方法 (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: 9f489835-6cda-4c8c-b139-079639a169cf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f3a6765bf5665704293233293982edfc1e746ce5
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927443"
---
# <a name="setresponsebuffering-method-sqlserverstatement"></a>setResponseBuffering 方法 (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  將這個 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 物件的回應緩衝模式設定為 **String full** 或 **adaptive** (不區分大小寫)。  
  
## <a name="syntax"></a>語法  
  
```  
  
public final void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>參數  
 *value*  
  
 **String**，包含回應緩衝模式。 有效模式可能是下列其中一個區分大小寫的 String：**full** 或 **adaptive**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 **adaptive** 會指定在必要時緩衝處理可能的資料下限。  
  
 **full** 會指定在執行階段從伺服器讀取整個結果。  
  
 adaptive 是 JDBC 驅動程式 2.0 和 3.0 版中的預設值。 full 是 JDBC 驅動程式 2.0 版之前的版本中的預設值。  
  
 [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) 可讓您覆寫目前 **SQLServerStatement** 物件的 **responseBuffering** 連線 [String](../../../connect/jdbc/reference/sqlserverstatement-class.md) 屬性。 如需使用回應緩衝模式的詳細資訊，請參閱[使用自適性緩衝](../../../connect/jdbc/using-adaptive-buffering.md)。  
  
 如果應用程式指定給 [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) 方法的參數值無效，則會擲回 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerStatement 成員](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 類別](../../../connect/jdbc/reference/sqlserverstatement-class.md)   
 [使用適應性緩衝](../../../connect/jdbc/using-adaptive-buffering.md)  
  
  
