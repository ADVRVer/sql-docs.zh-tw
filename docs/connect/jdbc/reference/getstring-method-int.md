---
title: getString 方法 (int) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getString (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f3fce8bf-8d6e-476f-aa6d-992daa79b899
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 92257f0941b34ffdf108b10debad55ce7532b98d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66773854"
---
# <a name="getstring-method-int"></a>getString 方法 (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  使用 Java 程式語言，並配合指定參數索引來擷取指定參數的值當作**字串**。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.lang.String getString(int index)  
```  
  
#### <a name="parameters"></a>參數  
 *index*  
  
 指出參數索引的 **int**。  
  
## <a name="return-value"></a>傳回值  
 **字串**值。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 getString 方法是由 java.sql.CallableStatement 介面中的 getString 方法指定。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的所有資料行都可以當作字串傳回。 這表示可以傳回所有數字和字元類型的字串表示法以及二進位資料行的十六進位字串表示法，例如 binary、varbinary、varbinary(max)、image、timestamp 和 uniqueidentifier。  
  
 區分位置的型別 (例如 money、smallmoney、datetime、smalldatetime、float、real、decimal 和 numeric) 將會針對該型別的基礎值傳回標準 toString() 格式。  
  
 使用者定義型別會當做十六進位字串值傳回。  
  
## <a name="see-also"></a>另請參閱  
 [getString 方法 &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getstring-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 成員](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement 類別](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
