---
title: FetchOptions 屬性 (RDS) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- FetchOptions property [ADO]
ms.assetid: 7b2e254a-9354-4541-bc98-bb185276388f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 19b266474c348af50db26fddafeea79d4cf33ade
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602558"
---
# <a name="fetchoptions-property-rds"></a>FetchOptions 屬性 (RDS)
表示非同步擷取的類型。  
  
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，RDS 伺服器元件不會再包含在 Windows 作業系統中 (請參閱 Windows 8 和[Windows Server 2012 相容性操作手冊](https://www.microsoft.com/download/details.aspx?id=27416)如需詳細資訊)。 RDS 用戶端元件將會在 Windows 的未來版本中移除。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該移轉至[WCF 資料服務](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="setting-and-return-values"></a>設定和傳回值  
 設定或傳回下列值之一。  
  
|常數|描述|  
|--------------|-----------------|  
|**adcFetchUpFront**|所有記錄[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)控制項傳回至應用程式之前提取。 完整**資料錄集**會擷取之前允許的應用程式做什麼。|  
|**adcFetchBackground**|控制項可以傳回給應用程式，只要在提取記錄的第一個批次。 後續的讀取**資料錄集**，嘗試存取不會擷取第一個批次中的記錄將會延遲，直到實際擷取的搜尋的記錄，在這段控制傳回到應用程式。|  
|**adcFetchAsync**|預設值。 控制會立即交還給應用程式中，而記錄會在背景擷取。 如果應用程式會嘗試讀取尚未尚未擷取的記錄，將讀取的最接近的搜尋記錄的記錄，並控制會立即傳回，表示目前結尾**資料錄集**已達到。 例如，呼叫[MoveLast](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)會實際擷取的最後一個記錄移動目前的記錄位置，即使多筆記錄會繼續填入**資料錄集**。|  
  
> [!NOTE]
>  這些常數會使用每個用戶端可執行檔必須提供它們的宣告。 您可以剪下並貼上您想要從檔案 Adcvbs.inc，位於 預設的安裝資料夾的 RDS 程式庫的常數宣告。  
  
## <a name="remarks"></a>備註  
 在 Web 應用程式中，您通常想要**adcFetchAsync** （預設值），因為它提供更佳的效能。 在已編譯的用戶端應用程式中，您通常想要**adcFetchBackground**。  
  
## <a name="applies-to"></a>適用於  
 [DataControl 物件 (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>另請參閱  
 [ExecuteOptions 和 FetchOptions 屬性範例 (VBScript)](../../../ado/reference/rds-api/executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Cancel 方法 (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)


