---
title: 資料來源屬性 (ADO) |Microsoft 文件
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::DataSource
helpviewer_keywords:
- DataSource property [ADO]
ms.assetid: 300a702a-3544-48c5-b759-83b511fe97e0
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f1481e3e8bd8076cfb18107d60cbbca78dc7da60
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="datasource-property-ado"></a>資料來源屬性 (ADO)
表示物件，包含表示為資料[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)物件。  
  
## <a name="remarks"></a>備註  
 這個屬性用來建立資料繫結控制項與資料環境。 資料環境會維護資料 （資料來源） 包含集合的具名物件 （資料成員），將會表示為**資料錄集**物件*。*  
  
 [DataMember](../../../ado/reference/ado-api/datamember-property.md)和**DataSource**屬性必須搭配使用。  
  
 參考的物件必須實作**IDataSource**介面，並且必須包含**IRowset**介面。  
  
## <a name="usage"></a>使用方式  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to.  
Set rs.DataSource = myDE      'Name of the object containing an IRowset.  
```  
  
## <a name="applies-to"></a>適用於  
 [Recordset 物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [DataMember 屬性](../../../ado/reference/ado-api/datamember-property.md)
