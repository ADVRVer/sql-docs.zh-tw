---
title: truncate 方法 (SQLServerBlob) |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerBlob.truncate
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ef181e04-003a-442a-9b7e-0c508a7cc873
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cd804132cff7897a780d6a17a26ce80fc2dd0fdf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="truncate-method-sqlserverblob"></a>truncate 方法 (SQLServerBlob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  依給定長度截斷 BLOB。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void truncate(long len)  
```  
  
#### <a name="parameters"></a>參數  
 *len*  
  
 BLOB 的新長度。  
  
## <a name="exceptions"></a>例外狀況  
 java.sql.SQLException  
  
## <a name="remarks"></a>備註  
 此截斷的方法是由 java.sql.Blob 介面中的 truncate 方法所指定。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerBlob 方法](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob 成員](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob 類別](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
