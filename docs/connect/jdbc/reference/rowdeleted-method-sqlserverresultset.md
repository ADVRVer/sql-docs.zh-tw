---
title: rowDeleted 方法 (SQLServerResultSet) |Microsoft Docs
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
- SQLServerResultSet.rowDeleted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9c6db315-e614-4604-b020-41af6a214cc1
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 90dc0d90de6c0ae55b29085b7658b7b71f21e32d
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786791"
---
# <a name="rowdeleted-method-sqlserverresultset"></a>rowDeleted 方法 (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取值，此值指出資料列是否已遭刪除。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean rowDeleted()  
```  
  
## <a name="return-value"></a>傳回值  
 如果資料列已經刪除且偵測到刪除，則為 **true**。 否則為 **false**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 rowDeleted 方法是由 java.sql.ResultSet 介面中的 rowDeleted 方法指定。  
  
 刪除的資料列可能會在結果集中留下可見的漏洞。 這個方法可用來偵測結果集中的漏洞。 傳回的值取決於這個 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 物件是否可以偵測到刪除。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會偵測所有可更新資料指標類型的資料列，雖然順向和動態資料指標的偵測作業屬於暫時性質。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
