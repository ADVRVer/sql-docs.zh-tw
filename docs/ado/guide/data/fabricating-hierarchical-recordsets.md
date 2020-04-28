---
title: 組裝階層式記錄集 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset fabrication [ADO]
- hierarchical Recordsets [ADO]
- fabricating hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: a584e642-a4a3-418e-bc20-3aff81a5625a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6fcdb630f2391f685080ac594cfdb537edf626a2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925329"
---
# <a name="fabricating-hierarchical-recordsets"></a>產生階層式資料錄集
下列範例顯示如何使用資料成形文法來定義父代、子系和孫**記錄集**的資料行，以製作沒有基礎資料來源的階層式記錄集。  
  
 若要製作階層式**記錄集**，您必須指定[OLE DB （ADO 服務提供者）（MSDataShape）的 Microsoft 資料成形服務](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)，而且可以在[連接](../../../ado/reference/ado-api/connection-object-ado.md)物件之[Open](../../../ado/reference/ado-api/open-method-ado-connection.md)方法的連接字串參數中指定 NONE 的 Data Provider 值。 如需詳細資訊，請參閱[資料成形的必要提供者](../../../ado/guide/data/required-providers-for-data-shaping.md)。  
  
```  
Dim cn As New ADODB.Connection  
Dim rsCustomers As New ADODB.Recordset  
  
cn.Open "Provider=MSDataShape;Data Provider=NONE;"  
  
strShape = _  
"SHAPE APPEND NEW adInteger AS CustID," & _  
            " NEW adChar(25) AS FirstName," & _  
            " NEW adChar(25) AS LastName," & _  
            " NEW adChar(12) AS SSN," & _  
            " NEW adChar(50) AS Address," & _  
         " ((SHAPE APPEND NEW adChar(80) AS VIN_NO," & _  
                        " NEW adInteger AS CustID," & _  
                        " NEW adChar(20) AS BodyColor, " & _  
                     " ((SHAPE APPEND NEW adChar(80) AS VIN_NO," & _  
                                    " NEW adChar(20) AS Make, " & _  
                                    " NEW adChar(20) AS Model," & _  
                                    " NEW adChar(4) AS Year) " & _  
                        " AS VINS RELATE VIN_NO TO VIN_NO))" & _  
            " AS Vehicles RELATE CustID TO CustID) "  
  
rsCustomers.Open strShape, cn, adOpenStatic, adLockOptimistic, -1  
```  
  
 一旦建立了**記錄集**，就可以填入、操作或保存在檔案中。  
  
## <a name="see-also"></a>另請參閱  
 [存取階層式記錄集中的資料列](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [正式圖形文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [資料成形所需的提供者](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Shape APPEND 子句](../../../ado/guide/data/shape-append-clause.md)   
 [一般 Shape 命令](../../../ado/guide/data/shape-commands-in-general.md)
