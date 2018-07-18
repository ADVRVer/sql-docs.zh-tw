---
title: 使用 Visual c + + 延伸模組 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ [ADO], using VC++ extensions
- ADO, Visual C++
ms.assetid: ff759185-df41-4507-8d12-0921894ffbd9
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 805abefbd6f934781b86060e98c73ab6ee8fd3c0
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982800"
---
# <a name="visual-c-extensions"></a>Visual c + + 延伸模組
## <a name="the-iadorecordbinding-interface"></a>IADORecordBinding 介面
 Microsoft Visual c + + Extensions for ADO 產生關聯或繫結欄位[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)C/c + + 變數的物件。 每當繫結的目前資料列**資料錄集**變更時中的所有繫結的欄位**資料錄集**會複製到 C/c + + 變數。 如有必要，複製的資料會轉換成 C/c + + 變數宣告的資料類型。

 **BindToRecordset**方法**IADORecordBinding**介面將欄位繫結至 C/c + + 變數。 **AddNew**方法會將新的資料列加入繫結**資料錄集**。 **更新**方法會填入新資料列中的欄位**資料錄集**，或使用 C/c + + 變數的值更新現有的資料列中的欄位。

 **IADORecordBinding**介面由實作**資料錄集**物件。 您不自行撰寫程式碼實作。

## <a name="binding-entries"></a>繫結項目
 Visual c + + 延伸模組，用於 ADO 對應的欄位[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)C/c + + 變數的物件。 欄位和變數之間的對應的定義會呼叫*繫結項目*。 巨集提供數值、 固定長度和可變長度的資料繫結項目。 自 Visual c + + 延伸模組類別，衍生類別中宣告的繫結項目和 C/c + + 變數**CADORecordBinding**。 **CADORecordBinding**類別在內部定義的繫結項目巨集。

 ADO 在內部對應至 OLE DB 中這些巨集的參數**DBBINDING**結構，並建立 OLE DB**存取子**物件來管理的移動和資料欄位與變數之間的轉換。 OLE DB 定義的資料為包含三個部分： A*緩衝區*其中儲存資料;*狀態*，指出欄位是否已成功儲存在緩衝區，或如何變數應該還原成欄位;而*長度*的資料。 (請參閱[開始和設定資料 (OLE DB)](http://msdn.microsoft.com/4369708b-c9fb-4d48-a321-bf949b41a369)在 OLE DB 程式設計人員參考中，如需詳細資訊。)

## <a name="header-file"></a>標頭檔
 若要使用 Visual c + + 延伸模組用於 ADO 應用程式中包含下列檔案：

```
#include <icrsint.h>
```

## <a name="binding-recordset-fields"></a>繫結資料錄集欄位

#### <a name="to-bind-recordset-fields-to-cc-variables"></a>資料錄集欄位繫結至 C/c + + 變數

1.  建立衍生自類別**CADORecordBinding**類別。

2.  在衍生類別中，指定繫結項目和對應的 C/c + + 變數。 括號之間的繫結項目**BEGIN_ADO_BINDING**並**END_ADO_BINDING**巨集。 請勿終止使用逗號或分號的巨集。 每個巨集自動指定適當的分隔符號。

     指定每個欄位對應至 C/c + + 變數的一個繫結項目。 使用適當的成員，從**ADO_FIXED_LENGTH_ENTRY**， **ADO_NUMERIC_ENTRY**，或**ADO_VARIABLE_LENGTH_ENTRY**系列巨集。

3.  在您的應用程式，建立衍生自類別的執行個體**CADORecordBinding**。 取得**IADORecordBinding**從介面**資料錄集**。 然後呼叫**BindToRecordset**方法來繫結**資料錄集**C/c + + 變數的欄位。

 如需詳細資訊，請參閱 < [Visual c + + Extensions 範例](../../../ado/guide/appendixes/visual-c-extensions-example.md)。

## <a name="interface-methods"></a>介面方法
 **IADORecordBinding**介面有三個方法： **BindToRecordset**， **AddNew**，以及**更新**。 每個方法的唯一引數是衍生自類別的執行個體的指標**CADORecordBinding**。 因此， **AddNew**並**更新**方法不能指定任何其 ADO 方法 namesakes 的參數。

## <a name="syntax"></a>語法
 **BindToRecordset**方法 associates**資料錄集**C/c + + 變數的欄位。

```
BindToRecordset(CADORecordBinding *binding)
```

 **AddNew**方法會叫用 adafruitis ADO [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)方法，來加入新的資料列**資料錄集**。

```
AddNew(CADORecordBinding *binding)
```

 **更新**方法會叫用 adafruitis ADO[更新](../../../ado/reference/ado-api/update-method.md)方法，來更新**資料錄集**。

```
Update(CADORecordBinding *binding)
```

## <a name="binding-entry-macros"></a>繫結項目巨集
 繫結項目巨集會定義的關聯**資料錄集**欄位和變數。 開始與結束的巨集分隔繫結項目集。

 系列的巨集可供固定長度的資料，例如**adDate**或是**adBoolean**; 數值資料，例如**adTinyInt**， **adInteger**，或**adDouble**; 和可變長度資料，例如**adChar**， **adVarChar**或**adVarBinary**。 所有的數字類型，除了**adVarNumeric**，也是固定長度類型。 每個系列的不同組的參數，以便您可以排除不感興趣的繫結資訊。

 如需詳細資訊，請參閱 <<c0> [ 附錄 a： 資料類型](http://msdn.microsoft.com/e3a0533a-2196-4eb0-a31e-92fe9556ada6)，OLE DB 程式設計人員參考。

### <a name="begin-binding-entries"></a>開始繫結項目
 **BEGIN_ADO_BINDING**(*類別*)

### <a name="fixed-length-data"></a>固定長度的資料
 **ADO_FIXED_LENGTH_ENTRY**(*序數、 資料型別、 緩衝區、 狀態、 修改*)

 **ADO_FIXED_LENGTH_ENTRY2**(*序數、 資料型別，緩衝區中，修改*)

### <a name="numeric-data"></a>數值資料
 **ADO_NUMERIC_ENTRY**(*序數、 資料型別、 緩衝區、 有效位數、 小數位數、 狀態、 修改*)

 **ADO_NUMERIC_ENTRY2**(*序數、 資料型別、 緩衝區、 有效位數、 小數位數的修改*)

### <a name="variable-length-data"></a>可變長度的資料
 **ADO_VARIABLE_LENGTH_ENTRY**(*序數、 資料型別、 緩衝區、 大小、 狀態、 長度、 修改*)

 **ADO_VARIABLE_LENGTH_ENTRY2**(*序數、 資料型別、 緩衝區、 大小、 狀態、 修改*)

 **ADO_VARIABLE_LENGTH_ENTRY3**(*序數、 資料型別、 緩衝區、 大小、 長度、 修改*)

 **ADO_VARIABLE_LENGTH_ENTRY4**(*序數、 資料型別、 緩衝區、 大小、 修改*)

### <a name="end-binding-entries"></a>結束繫結項目
 **END_ADO_BINDING**()

|參數|描述|
|---------------|-----------------|
|*類別*|類別定義的繫結項目和 C/c + + 變數。|
|*Ordinal*|序號，計算從一個**資料錄集**欄位都對應到您的 C/c + + 變數。|
|*資料類型*|C/c + + 變數的對等的 ADO 資料類型 (請參閱[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)取得一份有效的資料類型)。 值**資料錄集**欄位將會轉換成這個資料型別，如有必要。|
|*Buffer*|C/c + + 變數名稱，其中**資料錄集**欄位將會儲存。|
|*大小*|以位元組為單位的大小上限*緩衝區*。 如果*緩衝區*包含可變長度字串，其會允許出空間給結束的零。|
|*狀態*|會指出變數的名稱是否的內容*緩衝區*有效，以及是否要的欄位轉換*資料型別*已順利完成。<br /><br /> 兩個最重要的值，這個變數會**adFldOK**，表示轉換是否成功; 並**adFldNull**，這表示欄位的值會是類型 VT_NULL 的 VARIANT 和不只是空的。<br /><br /> 可能值為*狀態*詳列於下一步 資料表，也就是 「 狀態值 」。|
|*修改*|布林值旗標;如果為 TRUE，表示 ADO 都可以更新對應**Recordset**欄位中包含的值取代*緩衝區*。<br /><br /> 設定布林值*修改*為了讓 ADO 繫結的欄位中，更新，則為 TRUE 和 FALSE，如果您想要檢查的欄位，但無法變更它的參數。|
|*有效位數*|可以用來表示數值變數的數字的數目。|
|*小數位數*|數值變數中的小數位數。|
|*長度*|名稱的四個位元組，將包含變數中的資料的實際長度*緩衝區*。|

## <a name="status-values"></a>狀態值
 值*狀態*變數會指出欄位是否已成功地複製至的變數。

 設定資料，當*狀態*可能會設定為**adFldNull**表示**資料錄集**梇糔飶為 null。

|常數|值|描述|
|--------------|-----------|-----------------|
|**adFldOK**|0|傳回非 null 欄位值。|
|**adFldBadAccessor**|1|繫結無效。|
|**adFldCantConvertValue**|2|由於符號不符或資料溢位以外的原因，無法轉換值。|
|**adFldNull**|3|當取得欄位，表示已傳回 null 值。<br /><br /> 當設定的欄位，指出欄位應該設定為**NULL**欄位時無法編碼**NULL**本身 （例如，字元陣列或整數）。|
|**adFldTruncated**|4|已截斷可變長度的資料或數字。|
|**adFldSignMismatch**|5|值帶正負號和不帶正負號的變數資料類型。|
|**adFldDataOverFlow**|6|值大於可以儲存在變數資料類型。|
|**adFldCantCreate**|7|未知的資料行類型和欄位已經開啟。|
|**adFldUnavailable**|8|無法判斷欄位值 — 例如，在新的、 未指派的欄位沒有預設值。|
|**adFldPermissionDenied**|9|在更新時，沒有寫入資料的權限。|
|**adFldIntegrityViolation**|10|更新時，欄位值違反資料行的完整性。|
|**adFldSchemaViolation**|11|更新時，欄位值違反資料行結構描述。|
|**adFldBadStatus**|12|在更新時，無效的狀態參數。|
|**adFldDefault**|13|更新時，會使用預設值。|

## <a name="see-also"></a>另請參閱
 [Visual c + + 延伸模組範例](../../../ado/guide/appendixes/visual-c-extensions-example.md) [Visual c + + Extensions 標題](../../../ado/guide/appendixes/visual-c-extensions-header.md)
