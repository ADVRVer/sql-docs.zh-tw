---
title: CopyRecord 方法 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_CopyRecord
- _Record::CopyRecord
helpviewer_keywords:
- CopyRecord method [ADO]
ms.assetid: b9bcf272-3c74-479f-95dd-0229a32e98fc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d70dcba3d373b195950f90b6ef82c3d670844bb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63309209"
---
# <a name="copyrecord-method-ado"></a>CopyRecord 方法 (ADO)
複製所代表的實體[記錄](../../../ado/reference/ado-api/record-object-ado.md)到另一個位置。  
  
## <a name="syntax"></a>語法  
  
```  
  
Record.CopyRecord (Source, Destination, UserName, Password, Options, Async)  
```  
  
#### <a name="parameters"></a>參數  
 *Source*  
 選擇性。 A**字串**包含 URL 指定的實體来複製 （例如，檔案或目錄） 的值。 如果*來源*省略，或者指定為空字串、 檔案或目錄表示由目前[記錄](../../../ado/reference/ado-api/record-object-ado.md)會被複製。  
  
 *目的地*  
 選擇性。 A**字串**值，其中包含指定位置的 URL 位置*來源*會被複製。  
  
 *UserName*  
 選擇性。 A**字串**值，其中包含的使用者識別碼，如有需要授與存取權*目的地*。  
  
 *密碼*  
 選擇性。 A**字串**值，其中包含的密碼，如有需要請確認*UserName*。  
  
 *選項。*  
 選擇性。 A [CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md)值，其預設值為**adCopyUnspecified**。 指定此方法的行為。  
  
 *Async*  
 選擇性。 A**布林**值，當 **，則為 True**，指定此作業應該為非同步。  
  
## <a name="return-value"></a>傳回值  
 A**字串**值，通常會傳回的值*目的地*。 不過，確實傳回的值是提供者相依。  
  
## <a name="remarks"></a>備註  
 值*來源*並*目的地*不得相同，否則就會發生執行階段錯誤。 至少其中一個伺服器、 路徑或資源的名稱必須不同。  
  
 所有的子系 （例如，子目錄） 的*來源*會複製，遞迴地，除非**adCopyNonRecursive**指定。 在遞迴作業中，*目的地*不得的子目錄*來源*，否則將無法完成作業。  
  
 如果這個方法會失敗*目的地*識別現有的實體 （例如，檔案或目錄），除非**adCopyOverWrite**指定。  
  
> [!IMPORTANT]
>  使用**adCopyOverWrite**明智選項。 例如，將檔案複製到目錄時，指定這個選項會*刪除*目錄，並取代檔案。  
  
> [!NOTE]
>  使用 http 配置 Url 將會自動叫用[Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)。 如需詳細資訊，請參閱 <<c0> [ 絕對和相對 Url](../../../ado/guide/data/absolute-and-relative-urls.md)。  
  
## <a name="applies-to"></a>適用於  
 [Record 物件 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
