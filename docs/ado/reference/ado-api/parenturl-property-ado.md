---
title: ParentURL 屬性 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::ParentURL
helpviewer_keywords:
- ParentURL property [ADO]
ms.assetid: 65120ce6-3900-4cd4-b322-3b9816d74737
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 65704cea2a396e0f03de4bbcdc9f031f4c9af583
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703463"
---
# <a name="parenturl-property-ado"></a>ParentURL 屬性 (ADO)
表示絕對的 URL 字串，指向父代[記錄](../../../ado/reference/ado-api/record-object-ado.md)的目前**記錄**物件。  
  
## <a name="return-value"></a>傳回值  
 傳回**字串**值，指出父代的 URL**記錄**。  
  
## <a name="remarks"></a>備註  
 **ParentURL**屬性取決於用來開啟來源**記錄**物件。 例如，**記錄**可以使用包含相對路徑的目錄名稱所參考的來源開啟[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)屬性。  
  
 假設"first"下 「 第二個 「 包含的資料夾。 開啟**記錄**物件，使用下列語法：  
  
```  
record.ActiveConnection = "https://first"  
record.Open "second"  
```  
  
 現在的值`the` **ParentURL**屬性是`"https://first"`，則相同**ActiveConnection**。  
  
 來源也可以是絕對 URL 例如`"https://first/second"`。 **ParentURL**屬性就`"https://first"`，上面的層級`"second"`。  
  
 如果這個屬性可能是 null 的值：  
  
-   目前的物件; 沒有父系例如，如果**記錄**物件都代表目錄的根目錄。  
  
-   **記錄**物件都代表一個實體，不能指定的 url。  
  
 此屬性是唯讀的。  
  
> [!NOTE]
>  這個屬性只支援文件來源提供者，例如[Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)。 如需詳細資訊，請參閱 <<c0> [ 記錄和 Provider-Supplied 欄位](../../../ado/guide/data/records-and-provider-supplied-fields.md)。  
  
> [!NOTE]
>  使用 http 配置 Url 將會自動叫用[Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)。 如需詳細資訊，請參閱 <<c0> [ 絕對和相對 Url](../../../ado/guide/data/absolute-and-relative-urls.md)。  
  
> [!NOTE]
>  如果目前的記錄會包含從 ADO 資料錄**Recordset**，存取**ParentURL**屬性會導致執行階段錯誤訊息，指出沒有 URL，很有可能。  
  
## <a name="applies-to"></a>適用於  
 [Record 物件 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
