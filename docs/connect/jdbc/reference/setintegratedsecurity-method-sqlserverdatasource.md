---
title: setIntegratedSecurity 方法 (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setIntegratedSecurity
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4c968ee4-b041-424a-bf69-cc2c4a4f51c6
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7d922c2c2fcfadb6b7807b8d2845f8d3e6c5188c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66780450"
---
# <a name="setintegratedsecurity-method-sqlserverdatasource"></a>setIntegratedSecurity 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  設定 **Boolean** 值，這個值會指出是否啟用 integratedSecurity 屬性。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void setIntegratedSecurity(boolean enable)  
```  
  
#### <a name="parameters"></a>參數  
 *enable*  
  
 如果已啟用 integratedSecurity，則為 **true**， 否則為 **false**。  
  
## <a name="remarks"></a>Remarks  
 設為 "**true**"，以指出 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 將使用 Windows 認證來驗證應用程式的使用者。 如果為 "**true**"，則表示 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 將搜尋本機電腦認證快取，以找出在電腦或網路登入時已經提供的認證。 若為 "**false**"，則必須提供使用者名稱及密碼。  
  
> [!NOTE]  
>  只有在 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] Windows 作業系統上才支援這個屬性。  
  
 如需使用整合式的驗證的詳細資訊，請參閱[Building the Connection URL](../../../connect/jdbc/building-the-connection-url.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
