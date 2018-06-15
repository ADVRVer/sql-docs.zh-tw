---
title: getSelectMethod 方法 (SQLServerDataSource) |Microsoft 文件
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
- SQLServerDataSource.getSelectMethod
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6255d2e-0028-474a-afa8-553ef092243e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e68aa63db6b1bc5af9ea046e1501d25c5b1501bb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32838233"
---
# <a name="getselectmethod-method-sqlserverdatasource"></a>getSelectMethod 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  傳回所有結果集所建立的使用這項功能都使用的預設資料指標類型[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.lang.String getSelectMethod()  
```  
  
## <a name="return-value"></a>傳回值  
 A**字串**包含預設資料指標類型的值。  
  
## <a name="remarks"></a>備註  
 selectMethod 屬性會指定用於結果集的預設資料指標類型。 當您處理大型結果集而且不想要將完整結果集儲存在用戶端的記憶體內時，這個屬性會很實用。 將此屬性設定為 "cursor"，您就可以建立伺服器端資料指標，一次提取較小的資料區塊。 如果未設定 selectMethod 屬性，getSelectMethod 會傳回預設值 "direct"。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
