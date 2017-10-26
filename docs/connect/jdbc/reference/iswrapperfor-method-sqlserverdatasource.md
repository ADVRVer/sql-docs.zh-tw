---
title: "isWrapperFor 方法 (SQLServerDataSource) |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f77af027-c021-4a17-b264-1ee592bfdd84
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9d9537b797aefd83d1a09b90b37677e2a5c9b957
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="iswrapperfor-method-sqlserverdatasource"></a>isWrapperFor 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指出這個資料來源物件是否為指定之介面的包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### <a name="parameters"></a>參數  
 *iface*  
  
 A**類別**定義介面。  
  
## <a name="return-value"></a>傳回值  
 **true**如果此物件會實作介面或包裝實作介面的物件。 否則為 **false**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 [IsWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)方法和[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)方法由 JDBC 4.0 規格中導入的 java.sql.Wrapper 介面所定義。  
  
 如果這個方法會傳回 true，則呼叫[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)利用相同的引數將會成功。  
  
 如需詳細資訊，請參閱[包裝函式和介面](../../../connect/jdbc/wrappers-and-interfaces.md)。  
  
## <a name="see-also"></a>另請參閱  
 [unwrap 方法 &#40;SQLServerDataSource &#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)   
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

