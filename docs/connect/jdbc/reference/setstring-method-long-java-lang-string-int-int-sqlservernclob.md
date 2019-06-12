---
title: setString 方法 (long, java.lang.String, int, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2d5e9f50-15b2-4c76-8bfc-3b5be49c2781
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ad49b4a5e675d4ff6635583e0b64a1e57434ff22
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66762268"
---
# <a name="setstring-method-long-javalangstring-int-int-sqlservernclob"></a>setString 方法 (long, java.lang.String, int, int) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  依據指定的位移和長度，在指定位置的 NCLOB 開始位置寫入指定的字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
int setString(long pos,  
              java.lang.String str,  
              int offset,  
              int len)  
```  
  
#### <a name="parameters"></a>參數  
 *pos*  
  
 開始寫入至 **NCLOB** 的位置，第一個位置是 1。  
  
 *str*  
  
 要寫入至 **NCLOB** 的 String。  
  
 *offset*  
  
 *str* 內的位移，要開始讀取要寫入的字元。  
  
 *len*  
  
 要寫入的字元數。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 setString 方法是由 java.sql.PreparedStatement 介面中的 setString 方法指定。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerNClob 方法](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob 成員](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob 類別](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
