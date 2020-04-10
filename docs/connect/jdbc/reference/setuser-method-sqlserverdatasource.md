---
title: setUser 方法 (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setUser
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d2ea7906-2d10-438d-aa51-f576eea923c7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8ebf738906cbc717284a1b109f53de69e9af4eb8
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80901684"
---
# <a name="setuser-method-sqlserverdatasource"></a>setUser 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  設定用來連接到資料來源的使用者名稱。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void setUser(java.lang.String user)  
```  
  
#### <a name="parameters"></a>參數  
 *user*  
  
 包含使用者名稱的**字串**。  
  
## <a name="remarks"></a>備註  
 setUser 方法會設定將用來連線到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的使用者名稱。 如果未設定使用者名稱值，[getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md) 方法會傳回預設值 null。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDataSource 成員](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 類別](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
