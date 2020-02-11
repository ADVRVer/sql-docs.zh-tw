---
title: PageCount 屬性（ADO） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::PageCount
helpviewer_keywords:
- PageCount property [ADO]
ms.assetid: b601b56c-0ac4-44ee-bc91-c3d2d104f00a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ea893a019ab6d1333cecc5da5f1f66928467adfc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931789"
---
# <a name="pagecount-property-ado"></a>PageCount 屬性 (ADO)
指出[記錄集](../../../ado/reference/ado-api/recordset-object-ado.md)物件包含多少頁的資料。  
  
## <a name="return-value"></a>傳回值  
 傳回**Long**值，指出**記錄集中**的頁面數目。  
  
## <a name="remarks"></a>備註  
 使用**PageCount**屬性來判斷**記錄集**物件中的資料頁數目。 *頁面*是一組記錄，其大小等於[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)屬性設定。 即使最後一頁不完整，因為記錄數目比**PageSize**值少，因此會計算為**PageCount**值中的額外頁面。 如果**記錄集**物件不支援此屬性，則值會是-1，表示**PageCount**是未知深度。  
  
 如需頁面功能的詳細資訊，請參閱**PageSize**和[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)屬性。  
  
## <a name="applies-to"></a>套用至  
 [Recordset 物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [AbsolutePage、PageCount 和 PageSize 屬性範例（VB）](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage、PageCount 和 PageSize 屬性範例（VC + +）](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePage 屬性（ADO）](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [PageSize 屬性（ADO）](../../../ado/reference/ado-api/pagesize-property-ado.md)   
 [RecordCount 屬性 (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)
