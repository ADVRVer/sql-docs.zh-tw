---
title: setHostNameInCertificate 方法 (SQLServerDataSource) |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- setHostNameInCertificate Method (SQLServerDataSource)
apilocation:
- setHostNameInCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 2bcf4f2e-a103-4374-abc4-ffad4ce8e3c0
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aae071ffe1c3bee7017dfdf46440829d231207f4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="sethostnameincertificate-method-sqlserverdatasource"></a>setHostNameInCertificate 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  設定要用於驗證的主機名稱[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Secure Sockets Layer (SSL) 憑證。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void setHostNameInCertificate(java.lang.String hostNameInCertificate)  
```  
  
#### <a name="parameters"></a>參數  
 *hostNameInCertificate*  
  
 A**字串**，其中包含主機名稱。  
  
## <a name="remarks"></a>備註  
 此 hostNameInCertificate 值用來驗證[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]SSL 憑證時使用 SSL 加密通訊層。 預設值為 null。  
  
 如果 hostNameInCertificate 屬性設定為 null 或未指定，[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]會使用 serverName 屬性值來驗證[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]SSL 憑證。 如果 hostNameInCertificate 屬性設定為字串或是空字串 ""，驅動程式將會使用該值來驗證伺服器 SSL 憑證。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
