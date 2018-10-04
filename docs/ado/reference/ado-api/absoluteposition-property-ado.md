---
title: AbsolutePosition 屬性 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::AbsolutePosition
helpviewer_keywords:
- AbsolutePosition property [ADO]
ms.assetid: 79f8ee5e-fc70-46d8-8c29-ebf943c66592
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4444c54df6e3629e7f69e3fe0d54625f66c3e703
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47813156"
---
# <a name="absoluteposition-property-ado"></a>AbsolutePosition 屬性 (ADO)
指出的序數位置[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)物件的目前資料錄。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 針對 32 位元程式碼，設定或傳回**長**1 中的記錄數目的值**Recordset**物件 ([RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md))，或傳回的其中一個[PositionEnum](../../../ado/reference/ado-api/positionenum.md)值。  
  
 針對 64 位元程式碼，使用提供的 64 位元值的儲存體的資料類型。 例如，您可能會使用長時間或另一個值，例如 DBORDINAL 的 64 位元長度。 請勿使用**PositionEnum**值，因為它們被限制為 32 位元長度。  
  
## <a name="remarks"></a>備註  
 若要設定**AbsolutePosition**屬性，ADO 需要您使用的 OLE DB 提供者實作[IRowsetLocate:IRowset](https://msdn.microsoft.com/library/windows/desktop/ms721190.aspx)介面。  
  
 存取**AbsolutePosition**屬性**Recordset** ，以開啟 順向或動態資料指標就會引發錯誤**adErrFeatureNotAvailable**。 其他資料指標類型，正確的位置將會傳回，只要在 OLE DB 提供者支援**IRowsetScroll:IRowsetLocate**介面。 如果提供者不支援**IRowsetScroll**介面的屬性設定為**adPosUnknown**。 請參閱您的提供者，以判斷它是否支援的文件**IRowsetScroll**。  
  
 使用**AbsolutePosition**移至資料的屬性，根據其序數位置中**資料錄集**物件，或若要判斷目前的資料錄的序數位置。 提供者必須支援這個屬性才能使用適當的功能。  
  
 像是[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)屬性， **AbsolutePosition**是以 1 為基礎，並等於 1，當目前的記錄中的第一個記錄**資料錄集**。 您可以取得中的記錄總數**Recordset**物件[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)屬性。  
  
 當您設定**AbsolutePosition**屬性，即使它是目前的快取中的記錄 ADO 重新載入快取以一組新的記錄從您指定的記錄。 [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)屬性會決定此群組的大小。  
  
> [!NOTE]
>  您不應該使用**AbsolutePosition**屬性做 surrogate 的記錄數目。 當您刪除先前的記錄，就會變更指定記錄的位置。 另外還有指定的記錄會有相同的不保證**AbsolutePosition**如果**資料錄集**物件查詢，或重新開啟。 書籤仍會保留並傳回至指定位置的建議的方式，和是唯一的方法在所有類型的定位**資料錄集**物件。  
  
## <a name="applies-to"></a>適用於  
 [Recordset 物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [AbsolutePosition 和 CursorLocation 屬性範例 (VB)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vb.md)   
 [AbsolutePosition 和 CursorLocation 屬性範例 （VC + +）](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vc.md)   
 [AbsolutePage 屬性 (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [RecordCount 屬性 (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)
