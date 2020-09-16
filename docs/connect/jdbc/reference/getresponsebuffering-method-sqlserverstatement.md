---
description: getResponseBuffering 方法 (SQLServerStatement)
title: getResponseBuffering 方法 (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getResponseBuffering()
apilocation:
- SQLServerStatement.getResponseBuffering()
apitype: Assembly
ms.assetid: a9a9ffdd-7ce3-4e0a-907c-34d6a54e6865
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 08411235fe8e571e9f3bdaf7220f2387d3a0b5c0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434790"
---
# <a name="getresponsebuffering-method-sqlserverstatement"></a>getResponseBuffering 方法 (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取這個 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 物件的回應緩衝模式。  
  
## <a name="syntax"></a>語法  
  
```  
  
public final java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>傳回值  
 包含小寫 **full** 或 **adaptive** 的 **String**。  
  
## <a name="remarks"></a>備註  
 **adaptive** 會指定在必要時緩衝處理可能的資料下限。  
  
 **full** 會指定在執行階段從伺服器讀取整個結果。  
  
 **adaptive** 是 JDBC Driver 2.0 和 3.0 版中的預設值。 **full** 是 JDBC Driver 2.0 版之前的版本中的預設值。  
  
 如需使用回應緩衝模式的詳細資訊，請參閱[使用自適性緩衝](../../../connect/jdbc/using-adaptive-buffering.md)。  
  
## <a name="see-also"></a>另請參閱  
 [setResponseBuffering 方法 &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)   
 [SQLServerStatement 成員](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 類別](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
