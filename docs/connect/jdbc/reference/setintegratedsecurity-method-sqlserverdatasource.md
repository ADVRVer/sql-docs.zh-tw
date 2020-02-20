---
title: setIntegratedSecurity 方法 (SQLServerDataSource) | Microsoft Docs
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
ms.openlocfilehash: 79d9090df19851af3a778e23b7919f28081f32ef
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2020
ms.locfileid: "67974150"
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
  
## <a name="remarks"></a>備註  
 設為 "**true**"，以指出 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 將使用 Windows 認證來驗證應用程式的使用者。 如果為 "**true**"，則表示 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 將搜尋本機電腦認證快取，以找出在電腦或網路登入時已經提供的認證。 若為 "**false**"，則必須提供使用者名稱及密碼。  
  
> [!NOTE]  
>  只有在 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] Windows 作業系統上才支援這個屬性。  
  
 如需有關使用整合式驗證的詳細資訊，請參閱[建置連線 URL](../../../connect/jdbc/building-the-connection-url.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
