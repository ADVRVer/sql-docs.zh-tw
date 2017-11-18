---
title: "getBinaryStream 方法 (java.lang.String) |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerResultSet.getBinaryStream (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 149609b5-a6de-4e23-a440-7061775d0899
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ff004671c2e261d055b49e1a1de3b0643c1fc94b
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="getbinarystream-method-javalangstring"></a>getBinaryStream 方法 (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取值，這個目前的資料列內指定之資料行名稱的[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)當做不中斷位元組的二進位資料流的物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.io.InputStream getBinaryStream(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>參數  
 *columnName*  
  
 A**字串**，其中包含資料行名稱。  
  
## <a name="return-value"></a>傳回值  
 InputStream 物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 GetBinaryStream 方法 java.sql.ResultSet 介面中所指定此 getBinaryStream 方法。  
  
 這個方法可以只用於[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]binary、 varbinary、 varbinary （max） 和 image 資料型別。 嘗試搭配其他資料型別使用這個方法將會擲回例外狀況。  
  
 當這個方法以資料流形式取得值之後，該值可以在資料流的區塊中讀取。 這個方法特別適合用來擷取大型的 LONGVARBINARY 值。  
  
> [!NOTE]  
>  必須先讀取傳回之資料流中的所有資料，然後才可以取得其他任何資料行的值。 下一次呼叫 getter 方法時會以隱含方式關閉此資料流。 此外，資料流可以傳回 0 InputStream.available 方法呼叫時，是否有資料可用。  
  
## <a name="see-also"></a>另請參閱  
 [getBinaryStream 方法 &#40;SQLServerResultSet &#41;](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

