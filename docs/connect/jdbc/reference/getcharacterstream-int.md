---
title: getCharacterStream (int) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getCharacterStream(int paramIndex)
apilocation:
- SQLServerCallableStatement.getCharacterStream(int paramIndex)
apitype: Assembly
ms.assetid: eb20714b-52bc-4b6c-b23f-c9c3c9d73783
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 55fab0482e38afc175718a1b729d68124781dac9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953301"
---
# <a name="getcharacterstream-int"></a>getCharacterStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  透過給定的參數索引，擷取指定之參數的值來當做 java.io.Reader 物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
public final java.io.Reader getCharacterStream(int paramIndex)  
```  
  
#### <a name="parameters"></a>參數  
 *paramIndex*  
  
 指出參數索引的 **int**。  
  
## <a name="return-value"></a>傳回值  
 Reader 物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>另請參閱  
 [getCharacterStream 方法 &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 成員](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement 類別](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
