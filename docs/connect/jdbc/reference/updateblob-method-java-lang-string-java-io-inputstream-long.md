---
title: updateBlob 方法 (java.lang.String, java.io.InputStream, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 40f75549-5d5a-4de3-a271-4b8f0dd7b124
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ce47e805c8f4ffef67e239f8972c1296e1ef5adb
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80903317"
---
# <a name="updateblob-method-javalangstring-javaioinputstream-long"></a>updateBlob 方法 (java.lang.String, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  使用指定的輸入資料流來更新指定的資料行，該值將包含指定的位元組數目。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void updateBlob(java.lang.String columnLabel,  
                       java.io.InputStream inputStream)  
                                              long length)  
```  
  
#### <a name="parameters"></a>參數  
 *columnLabel*  
  
 **String**，包含資料行標籤。  
  
 *inputStream*  
  
 InputStream 物件。  
  
 *length*  
  
 **long**，指出資料流的長度。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 updateBlob 方法是由 java.sql.ResultSet 介面中的 updateBlob 方法指定。  
  
## <a name="see-also"></a>另請參閱  
 [updateBlob 方法 &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)   
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
