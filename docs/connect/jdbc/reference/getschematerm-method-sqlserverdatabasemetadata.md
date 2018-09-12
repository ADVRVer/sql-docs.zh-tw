---
title: getSchemaTerm 方法 (SQLServerDatabaseMetaData) |Microsoft Docs
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
- SQLServerDatabaseMetaData.getSchemaTerm
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3e4a400f-0859-4ac3-983e-c25633b33683
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dfa14c040aa8c399fa4993fe68347ffe61ee8f7b
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785606"
---
# <a name="getschematerm-method-sqlserverdatabasemetadata"></a>getSchemaTerm 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取慣用詞彙做為這個資料庫中的「目錄」。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.lang.String getSchemaTerm()  
```  
  
## <a name="return-value"></a>傳回值  
 **String**，包含慣用詞彙。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 getSchemaTerm 方法是由 java.sql.DatabaseMetaData 介面中 getSchemaTerm 方法指定。  
  
 當搭配 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫使用 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 時，這個方法會傳回作為慣用詞彙的 "schema"。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成員](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 類別](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
