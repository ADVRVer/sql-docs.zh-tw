---
title: Open 方法 (ADO Record) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_Open
- _Record::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: ab79a623-88a9-40b6-a017-a658bf19b778
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b4d105d648c7877e7099dea637c2a2c6a094985f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63241091"
---
# <a name="open-method-ado-record"></a>Open 方法 (ADO Record)
開啟現有[記錄](../../../ado/reference/ado-api/record-object-ado.md)物件，或建立新的項目所代表**記錄**，例如檔案或目錄。  
  
## <a name="syntax"></a>語法  
  
```  
  
Open Source, ActiveConnection, Mode, CreateOptions, Options, UserName, Password  
```  
  
#### <a name="parameters"></a>參數  
 *Source*  
 選擇性。 A **Variant**可能代表之實體的 URL，這由**記錄**物件**命令**，開啟[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)或另一個**記錄**物件，包含在 SQL SELECT 陳述式或資料表名稱的字串。  
  
 *ActiveConnection*  
 選擇性。 A **Variant**表示的連接字串或開放[連線](../../../ado/reference/ado-api/connection-object-ado.md)物件。  
  
 *模式*  
 選擇性。 A [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md)值，指定結果的存取模式**記錄**物件。 預設值是**adModeUnknown**。  
  
 *CreateOptions*  
 選擇性。 A [RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md)值，指定是否應該開啟現有的檔案或目錄，或應該建立新的檔案或目錄。 預設值是**adFailIfNotExists**。 如果設為預設值，存取模式取自[模式](../../../ado/reference/ado-api/mode-property-ado.md)屬性。 會忽略這個參數時*來源*參數不包含 URL。  
  
 *選項。*  
 選擇性。 A [RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md)值，指定開啟選項**記錄**。 預設值是**adOpenRecordUnspecified**。 可以結合這些值。  
  
 *UserName*  
 選擇性。 A**字串**值，其中包含的使用者識別碼，如有必要，授與存取權*來源*。  
  
 *密碼*  
 選擇性。 A**字串**值，其中包含的密碼，如有必要，請確認*UserName*。  
  
## <a name="remarks"></a>備註  
 *來源*可能是：  
  
-   URL 中。 如果 URL 的通訊協定為 http 時，網際網路提供者會叫用預設值。 如果 URL 指向包含可執行的指令碼的節點 (例如。ASP 網頁，）**記錄**，其中包含的來源，而非執行預設會開啟內容。 使用*選項*引數來修改此行為。  
  
-   A**記錄**物件。 A**記錄**從另一個開啟的物件**記錄**會複製原始**記錄**物件。  
  
-   A**命令**物件。 開啟**記錄**物件表示由執行的單一資料列**命令**。 如果結果包含多個單一資料列，第一個資料列的內容會放在記錄和錯誤可能會加入**錯誤**集合。  
  
-   在 SQL SELECT 陳述式。 開啟**記錄**物件表示由執行字串內容的單一資料列。 如果結果包含多個單一資料列，第一個資料列的內容會放在記錄和錯誤可能會加入**錯誤**集合。  
  
-   資料表名稱。  
  
 如果**記錄**物件都代表一個實體，無法存取的 url (例如，資料列**資料錄集**衍生自資料庫)，兩者的值[ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)屬性和欄位，以存取**adRecordURL**常數都是 null。  
  
> [!NOTE]
>  使用 http 配置 Url 將會自動叫用[Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)。 如需詳細資訊，請參閱 <<c0> [ 絕對和相對 Url](../../../ado/guide/data/absolute-and-relative-urls.md)。  
  
## <a name="applies-to"></a>適用於  
 [Record 物件 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [Open 方法 (ADO Connection)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open 方法 (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open 方法 (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema 方法](../../../ado/reference/ado-api/openschema-method.md)
