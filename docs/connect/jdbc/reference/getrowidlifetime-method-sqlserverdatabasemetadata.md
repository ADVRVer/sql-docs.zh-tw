---
title: getRowIdLifetime 方法 (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 317c0b44-fe3f-4142-9cab-e40e4c4fe070
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7aa2b4f740795169824cb4962f17c2dfecdc7974
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66762532"
---
# <a name="getrowidlifetime-method-sqlserverdatabasemetadata"></a>getRowIdLifetime 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  傳回狀態，此狀態會指出是否支援 SQL RowId 資料類型。 如果支援，將傳回 RowId 物件維持有效的存留期間。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.sql.RowIdLifetime getRowIdLifetime()  
```  
  
## <a name="return-value"></a>傳回值  
 RowIdLifetime 物件。  
  
> [!NOTE]  
>  在 JDBC 驅動程式 2.0 版中，這個方法會傳回 java.sql.RowIdLifetime.ROWID_UNSUPPORTED 值。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 getRowIdLifetime 方法是由 java.sql.DatabaseMetaData 介面中 getRowIdLifetime 方法指定。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成員](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 類別](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
