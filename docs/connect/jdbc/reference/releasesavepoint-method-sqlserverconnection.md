---
title: releaseSavepoint 方法 (SQLServerConnection) |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.releaseSavepoint
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6b625ea-c7ce-4a32-a9e0-6d2b4321bfd8
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 63704b974e2eb83c77a075d4ffba1d8498f2c7e9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32843523"
---
# <a name="releasesavepoint-method-sqlserverconnection"></a>releaseSavepoint 方法 (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  移除指定[SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)物件從目前的交易。  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 目前不支援這個方法。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void releaseSavepoint(java.sql.Savepoint savepoint)  
```  
  
#### <a name="parameters"></a>參數  
 *儲存點*  
  
 要移除儲存點物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 ReleaseSavepoint 方法 java.sql.Connection 介面中所指定此 releaseSavepoint 方法。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerConnection 成員](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection 類別](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
