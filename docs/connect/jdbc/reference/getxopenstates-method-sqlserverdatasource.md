---
title: getXopenStates 方法 (SQLServerDataSource) |Microsoft 文件
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
ms.topic: article
apiname:
- SQLServerDataSource.getXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de6fdf6b-8345-4490-b35e-7115b61e782e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 060b148d8cb0b8139b9ed5cd45fa698852cc1ae5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="getxopenstates-method-sqlserverdatasource"></a>getXopenStates 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  傳回**布林**值，指出是否啟用將 SQL 狀態轉換成 XOPEN 標準狀態。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean getXopenStates()  
```  
  
## <a name="return-value"></a>傳回值  
 **true**如果啟用將 SQL 狀態轉換成 XOPEN 標準狀態。 否則為 **false**。  
  
## <a name="remarks"></a>備註  
 如果 xopenStates 屬性設定為**true**、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]會將 SQL 狀態轉換成 XOPEN 標準狀態。 預設值是**false**，因而導致 JDBC 驅動程式來產生 SQL 99 狀態碼。 如果 xopenStates 未設定，getXopenStates 方法會傳回預設值的**false**。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
