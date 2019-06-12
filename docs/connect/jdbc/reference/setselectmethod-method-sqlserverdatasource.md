---
title: setSelectMethod 方法 (SQLServerDataSource) |Microsoft Docs
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
manager: jroth
ms.openlocfilehash: c48aabcb618ba16c0769210903318b0d386d941d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66767851"
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
  
## <a name="remarks"></a>Remarks  
 selectMethod 是用於結果集的預設資料指標類型。 當您處理大型結果集而且不想要將完整結果集儲存在用戶端的記憶體內時，這個屬性會很實用。 將此屬性設定為 "cursor"，您就可以建立伺服器端資料指標，一次提取較小的資料區塊。 如果未設定 selectMethod 屬性，[getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md) 會傳回預設值 "direct"。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
