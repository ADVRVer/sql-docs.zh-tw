---
title: 保存階層式資料錄集 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchical Recordsets [ADO], persisting
- persisting hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: 43798bb5-98a6-4ad6-9bf8-78154b3a1827
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2db4e4b4d3d7d137f4f033e35dd643cb0a2d11bb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47666626"
---
# <a name="persisting-hierarchical-recordsets"></a>保存階層式資料錄集
您可以儲存階層式**Recordset** ADTG 或 XML 格式，藉由呼叫中的檔案[儲存](../../../ado/reference/ado-api/save-method.md)方法。 不過，兩個的限制時儲存階層式**資料錄集**中的 XML 格式： 如果無法儲存在 XML 階層**資料錄集**包含擱置的更新，和您不能以參數化的方式儲存階層式**資料錄集**。  
  
 如需資料成形的提供者的詳細資訊，請參閱[Microsoft Data Shaping Service 的 OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (ADO) 和[OLE DB Data Shaping Service 的概觀](http://msdn.microsoft.com/9f51e471-8e85-448e-9fb8-b64bbf767bf3)。  
  
## <a name="see-also"></a>另請參閱  
 [資料成形範例](../../../ado/guide/data/data-shaping-example.md)   
 [正式 Shape 文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [一般 Shape 命令](../../../ado/guide/data/shape-commands-in-general.md)
