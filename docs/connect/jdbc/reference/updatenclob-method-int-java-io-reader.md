---
title: updateNClob 方法 （int，java.io.Reader） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 17adafd4-3ac3-4ff0-af9d-f087cc5ef936
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d5bf40ccd10d1c97728feadbb8a3d1c5512df070
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47612116"
---
# <a name="updatenclob-method-int-javaioreader"></a>updateNClob 方法 (int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  使用指定的 **Reader** 物件，更新指定的資料行。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void updateNClob(int columnIndex,  
                        java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>參數  
 *columnIndex*  
  
 指出資料行索引的 **int**。  
  
 *reader*  
  
 讀取器物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 UpdateNClob 方法 java.sql.ResultSet 介面中所指定這個 updateNClob 方法。  
  
 這個方法僅支援**nvarchar （max)**， **ntext**，並**xml**資料行。 對任何其他資料類型使用這個方法，將擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [updateNClob 方法 &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)   
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
