---
title: "getEncrypt 方法 (SQLServerDataSource) |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- getEncrypt Method (SQLServerDataSource)
apilocation:
- getEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 1cdb12dd-6e6f-4bbd-8f5f-9e630f3ee2c9
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c8edaf27e2c08b1738d8dedc3e059c0fecb5043b
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="getencrypt-method-sqlserverdatasource"></a>getEncrypt 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  傳回**布林**值，指出是否啟用 encrypt 屬性。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean getEncypt()  
```  
  
## <a name="return-value"></a>傳回值  
 **true**如果加密已啟用。 否則為 **false**。  
  
## <a name="remarks"></a>備註  
 如果 encrypt 屬性設定為**true**、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]可確保[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]如果伺服器已安裝憑證，用戶端與伺服器之間傳送的所有資料使用 SSL 加密。  
  
 如果 encrypt 屬性未指定或設為**false**，驅動程式不會強制執行[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]支援 SSL 加密。 如果[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]執行個體未設定為強制 SSL 加密，不用任何加密建立連線。 如果[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]執行個體設定為強制 SSL 加密，[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]會自動啟用 SSL 加密時正確設定上執行 Java Virtual Machine (JVM)，否則連接會中止而且驅動程式將會引發發生錯誤。 如果未設定 encryption 屬性， [getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md)方法會傳回預設值**false**。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
