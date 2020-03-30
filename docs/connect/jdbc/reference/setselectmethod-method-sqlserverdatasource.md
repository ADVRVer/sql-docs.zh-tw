---
title: setSelectMethod 方法 (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setSelectMethod
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7934276d-5ac9-4cbc-a2a0-2c65c93733ac
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e82bdcef16c854d0bcc1f11757b0bb2ed6030145
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "67973006"
---
# <a name="setselectmethod-method-sqlserverdatasource"></a>setSelectMethod 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  設定所有結果集所使用的預設資料指標類型，這些結果集是使用這個 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) 物件所建立。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void setSelectMethod(java.lang.String selectMethod)  
```  
  
#### <a name="parameters"></a>參數  
 *selectMethod*  
  
 **String** 值，其中包含預設資料指標類型。  
  
## <a name="remarks"></a>備註  
 selectMethod 是用於結果集的預設資料指標類型。 當您處理大型結果集而且不想要將完整結果集儲存在用戶端的記憶體內時，這個屬性會很實用。 將此屬性設定為 "cursor"，您就可以建立伺服器端資料指標，一次提取較小的資料區塊。 如果未設定 selectMethod 屬性，[getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md) 會傳回預設值 "direct"。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
