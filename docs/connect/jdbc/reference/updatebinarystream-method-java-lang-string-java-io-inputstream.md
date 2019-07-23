---
title: updateBinaryStream 方法 (java.io.InputStream) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 56883144-26a0-4f45-ad36-4f616369af3e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bc247cd3f97aeebeb6f52e1b4f3f36d8d97f6548
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997156"
---
# <a name="updatebinarystream-method-javalangstring-javaioinputstream"></a>updateBinaryStream 方法 (java.lang.String, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  使用二進位資料流值，更新指定的資料行。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void updateBinaryStream(java.lang.String columnLabel,  
                               java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>參數  
 *columnLabel*  
  
 **String**，包含資料行標籤。  
  
 *x*  
  
 InputStream 物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 updateBinaryStream 方法是由 sql-dmo 介面中的 updateBinaryStream 方法指定。  
  
 針對**image**、 **text**和**Ntext** SQL Server 資料類型使用這個方法可能會影響效能。  
  
 這個方法會透過 InputStream 物件將位元組傳遞到選取的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 二進位資料行，例如 binary、varbinary、varbinary(max)、image、xml 和 udt。 這個方法不支援更新字元資料行。 若要以 InputStream 更新字元資料行，請使用 [updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md) 方法。  
  
## <a name="see-also"></a>另請參閱  
 [updateBinaryStream 方法 &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
