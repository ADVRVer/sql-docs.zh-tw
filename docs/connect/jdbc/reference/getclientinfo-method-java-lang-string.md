---
title: getClientInfo 方法 (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e8e632c4-d6cc-4c5e-b6ad-873579343b19
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 82dee3b10241abf2cfb014d4617d2ae2c5588eae
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80907479"
---
# <a name="getclientinfo-method-javalangstring"></a>getClientInfo 方法 (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取指定之用戶端資訊屬性的值。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.lang.String getClientInfo (java.lang.String name)  
```  
  
#### <a name="parameters"></a>參數  
 *name*  
  
 String，包含要擷取之用戶端資訊屬性的名稱。  
  
## <a name="return-value"></a>傳回值  
 String，包含用戶端資訊屬性的值。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 getClientInfo 方法是由 java.sql.Connection 介面中的 getClientInfo 方法所指定。  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 不支援任何用戶端資訊屬性。 因此，此方法會傳回 **null**。  
  
 同樣地，應用程式可以使用 [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) 類別的 [getClientInfoProperties](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) 方法，擷取驅動程式可支援的用戶端資訊屬性清單。 [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) 方法會傳回空的結果集。  
  
## <a name="see-also"></a>另請參閱  
 [getClientInfo 方法 &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection 成員](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection 類別](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
