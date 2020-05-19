---
title: URL 屬性（RDS） |Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- URL property [ADO]
ms.assetid: 8c56b233-1be8-442c-8d0e-a4c96465bc99
author: rothja
ms.author: jroth
ms.openlocfilehash: 09785fde3531d50f33064415ddc769eb07f0fec2
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2020
ms.locfileid: "82750522"
---
# <a name="url-property-rds"></a>URL 屬性 (RDS)
表示包含相對或絕對 URL 的字串。  
  
 您可以在設計階段于[DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)物件的物件標記中，或在執行時間的腳本程式碼中設定**URL**屬性。  
  
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，Windows 作業系統不再包含 RDS 伺服器元件（如需詳細資訊，請參閱 Windows 8 和[Windows Server 2012 相容性操作手冊](https://www.microsoft.com/download/details.aspx?id=27416)）。 RDS 用戶端元件將會在未來的 Windows 版本中移除。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該遷移至[WCF 資料服務](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="syntax"></a>語法  
  
```  
  
Design time: <PARAM NAME="URL" VALUE="Server">  
Run time: DataControl.URL="Server"  
```  
  
#### <a name="parameters"></a>參數  
 *Server*  
 包含有效 URL 的**字串**值。  
  
 *DataControl*  
 代表**DataControl**物件的物件變數。  
  
## <a name="remarks"></a>備註  
 通常，URL 會識別可產生並傳回[記錄集](../../../ado/reference/ado-api/recordset-object-ado.md)的 Active Server Page （.asp）檔案。 因此，使用者可以取得**記錄集**，而不需要叫用伺服器端[DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)物件，或編寫自訂的商務物件。  
  
 如果已設定**url**屬性， [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md)會將變更提交至 url 所指定的位置。  
  
## <a name="applies-to"></a>套用至  
 [DataControl 物件 (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>另請參閱  
 [URL 屬性範例 (VBScript)](../../../ado/reference/rds-api/url-property-example-vbscript.md)


