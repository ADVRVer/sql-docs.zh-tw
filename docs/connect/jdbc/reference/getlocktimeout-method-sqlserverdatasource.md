---
title: getLockTimeout 方法 (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 676094e9-ec18-4524-9b21-1f9c5b16dd52
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f9c94e0c69bd528f1c579f41319a4db18b7d4d3c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67982566"
---
# <a name="getlocktimeout-method-sqlserverdatasource"></a>getLockTimeout 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  傳回 **int** 值，這個值指出資料庫在報告鎖定逾時之前所要等候的毫秒數。  
  
## <a name="syntax"></a>語法  
  
```  
  
public int getLockTimeout()  
```  
  
## <a name="return-value"></a>傳回值  
 **int** 值，其中包含資料庫要等候的毫秒數。  
  
## <a name="remarks"></a>Remarks  
 鎖定逾時是等候資料庫報告鎖定逾時的毫秒數。預設值為 -1，表示將會無限期地等候。 如果已指定，則此值為連接上所有陳述式的預設值。  
  
> [!NOTE]  
>  0 值表示不會等候。 如果未設定 lockTimeout 屬性，getLockTimeout 方法會傳回預設值 -1。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
