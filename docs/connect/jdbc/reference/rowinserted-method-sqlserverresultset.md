---
title: rowInserted 方法 (SQLServerResultSet) |Microsoft Docs
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
- SQLServerResultSet.rowInserted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e7c10372-0be8-4baa-87f7-ed6b66003357
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5b11d932eab77c0987d605b6914666e58d1d3b06
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785255"
---
# <a name="rowinserted-method-sqlserverresultset"></a>rowInserted 方法 (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取值，此值指出目前資料列是否具有插入。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean rowInserted()  
```  
  
## <a name="return-value"></a>傳回值  
 如果資料列具有插入且偵測到插入，則為 **true**， 否則為 **false**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 rowUpdated 方法是由 java.sql.ResultSet 介面中的 rowUpdated 方法指定。  
  
 傳回的值取決於這個 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 物件是否可以偵測到可見的插入。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不會偵測任何資料指標類型的插入資料列。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
