---
title: "AddNew 方法 (ADO) |Microsoft 文件"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::AddNew
- Recordset15::raw_AddNew
helpviewer_keywords:
- AddNew method [ADO]
ms.assetid: a9f54be9-5763-45d0-a6eb-09981b03bc08
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b804e2c2ea92a2f1f10caf98a556de3ff1a8fca4
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="addnew-method-ado"></a>AddNew 方法 (ADO)
建立可更新的新記錄[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
recordset.AddNew FieldList, Values  
```  
  
#### <a name="parameters"></a>參數  
 *資料錄集*  
 A**資料錄集**物件。  
  
 *FieldList*  
 選擇性。 使用單一名稱或名稱的陣列或欄位的新記錄中的序數位置。  
  
 *值*  
 選擇性。 單一值，則為陣列的新記錄中欄位的值。 如果*Fieldlist*屬於陣列、*值*也必須是陣列具有相同數目的成員; 否則就會發生錯誤。 欄位名稱的順序必須符合的每個陣列中的欄位值的順序。  
  
## <a name="remarks"></a>備註  
 使用**AddNew**方法來建立並初始化新的記錄。 使用[支援](../../../ado/reference/ado-api/supports-method.md)方法**adAddNew** ( [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)值) 以確認是否可以將記錄加入至目前**資料錄集**物件。  
  
 在您呼叫後**AddNew**方法，新的記錄變成目前的記錄，並且目前之後呼叫[更新](../../../ado/reference/ado-api/update-method.md)方法。 因為新的記錄會附加至**資料錄集**，呼叫**MoveNext**更新之後將結尾移動**資料錄集**，使得**EOF** ，則為 true。 如果**資料錄集**物件不支援書籤，您可能無法存取新的記錄，一旦您移到另一筆記錄。 根據您的資料指標類型，您可能需要呼叫[Requery](../../../ado/reference/ado-api/requery-method.md) ，使新的記錄可存取的方法。  
  
 如果您呼叫**AddNew** ADO 編輯目前的記錄時，或加入新的記錄時，呼叫**更新**方法來儲存任何變更，並接著會建立新的記錄。  
  
 行為**AddNew**方法而定的更新模式**資料錄集**物件和是否傳遞*Fieldlist*和*值*引數。  
  
 在*立即更新模式*(在其中提供者將變更寫入基礎資料來源一旦呼叫**更新**方法)，則呼叫**AddNew**不含方法引數集[EditMode](../../../ado/reference/ado-api/editmode-property.md)屬性**adEditAdd** ( [EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md)值)。 提供者會快取所有欄位值變更在本機。 呼叫**更新**方法張貼新的記錄，到資料庫，並重設**EditMode**屬性**adEditNone** ( **EditModeEnum**值)。 如果您要傳入*Fieldlist*和*值*引數，ADO 會立即發佈新的記錄，到資料庫 (沒有**更新**呼叫是必要的); **EditMode**屬性值不會變更 (**adEditNone**)。  
  
 在*批次更新模式*(其中提供者會快取多個變更，並將它們寫入基礎資料來源，只有當您呼叫[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)方法)，則呼叫**AddNew**方法沒有引數集**EditMode**屬性**adEditAdd**。 提供者會快取所有欄位值變更在本機。 呼叫**更新**方法會將新的記錄加入至目前**資料錄集**，但提供者不會將變更公佈到基礎資料庫中，或重設**EditMode**若要**adEditNone**，直到您呼叫**UpdateBatch**方法。 如果您要傳入*Fieldlist*和*值*引數，ADO 就會將新的記錄傳送至快取和集合中的存放裝置提供者**EditMode**至**adEditAdd**; 您需要呼叫**UpdateBatch**張貼至基礎資料庫的新記錄的方法。  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用欄位清單與包含中，以了解如何包含在欄位清單及值清單，做為陣列的值清單 AddNew 方法。  
  
```  
create table aa1 (intf int, charf char(10))  
insert into aa1 values (2, 'aa')  
  
Dim cn As New adodb.Connection  
Dim rs As New adodb.Recordset  
Dim cmd As New adodb.Command  
  
cn.ConnectionString = "Provider=SQLOLEDB;Data Source=alexverb2;uid=sa;pwd=foo$bar00;"  
  
cn.Open  
rs.Open "select * from xxx..aa1", cn, adOpenKeyset, adLockOptimistic  
  
Dim fieldsArray(1) As Variant  
fieldsArray(0) = "intf"  
fieldsArray(1) = "charf"  
Dim values(1) As Variant  
values(0) = 4  
values(1) = "as"  
rs.AddNew fieldsArray, values  
rs.Update  
```  
  
## <a name="applies-to"></a>適用於  
 [資料錄集物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [AddNew 方法範例 (VB)](../../../ado/reference/ado-api/addnew-method-example-vb.md)   
 [AddNew 方法範例 (VBScript)](../../../ado/reference/ado-api/addnew-method-example-vbscript.md)   
 [AddNew 方法範例 （VC + +）](../../../ado/reference/ado-api/addnew-method-example-vc.md)   
 [CancelUpdate 方法 (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [EditMode 屬性](../../../ado/reference/ado-api/editmode-property.md)   
 [Requery 方法](../../../ado/reference/ado-api/requery-method.md)   
 [支援方法](../../../ado/reference/ado-api/supports-method.md)   
 [Update 方法](../../../ado/reference/ado-api/update-method.md)   
 [UpdateBatch 方法](../../../ado/reference/ado-api/updatebatch-method.md)

