---
title: getBinaryStream 方法 (int) |Microsoft Docs
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
- SQLServerResultSet.getBinaryStream (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de22a6c4-1ba3-4ed0-91a2-bf235c2ceec3
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6cae82023ce19760ae3ed324458f6a6fae6e46f3
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784709"
---
# <a name="getbinarystream-method-int"></a>getBinaryStream 方法 (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  從這個 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 物件目前資料列中擷取指定資料行索引值來當作不中斷位元組的二進位資料流。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.io.InputStream getBinaryStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>參數  
 *columnIndex*  
  
 指出資料行索引的 **int**。  
  
## <a name="return-value"></a>傳回值  
 InputStream 物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 GetBinaryStream 方法 java.sql.ResultSet 介面中所指定這個 getBinaryStream 方法。  
  
 這個方法只能搭配 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料類型 binary、varbinary、varbinary(max) 和 image 使用。 嘗試搭配其他資料型別使用這個方法將會擲回例外狀況。  
  
 當這個方法以資料流形式取得值之後，該值可以在資料流的區塊中讀取。 這個方法特別適合用來擷取大型的 LONGVARBINARY 值。  
  
> [!NOTE]  
>  必須先讀取傳回之資料流中的所有資料，然後才可以取得其他任何資料行的值。 下一次呼叫 getter 方法時會以隱含方式關閉此資料流。 此外，當呼叫 InputStream.available 方法時，資料流可以傳回 0，不論是否有資料可用。  
  
## <a name="see-also"></a>另請參閱  
 [getBinaryStream 方法 &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
