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
manager: craigg
ms.openlocfilehash: 629c92aaf5ffb23976ad2e4ff2377cc53f87120d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842556"
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
  
 **String** 值，包含預設資料指標類型。  
  
## <a name="remarks"></a>Remarks  
 selectMethod 是用於結果集的預設資料指標類型。 當您處理大型結果集而且不想要將完整結果集儲存在用戶端的記憶體內時，這個屬性會很實用。 將此屬性設定為 "cursor"，您就可以建立伺服器端資料指標，一次提取較小的資料區塊。 如果未設定 selectMethod 屬性，[getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md) 會傳回預設值 "direct"。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
