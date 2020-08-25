---
description: Refresh 方法 (RDS)
title: " (RDS) 的 Refresh 方法 |Microsoft Docs"
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
f1_keywords:
- Refresh
- RDS.DataControl::Refresh
- DataControl::Refresh
helpviewer_keywords:
- Refresh method [RDS]
ms.assetid: c90a8050-0ff4-4c83-9925-261f2f2ccfe9
author: rothja
ms.author: jroth
ms.openlocfilehash: b55794815808b65ae4ad7f1dc5cc684360766aa8
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "88767547"
---
# <a name="refresh-method-rds"></a>Refresh 方法 (RDS)
重新查詢 [Connect](./connect-property-rds.md) 屬性中指定的資料來源，並更新查詢結果。  
  
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，Windows 作業系統中不再包含 RDS 伺服器元件 (如需詳細) 資訊，請參閱 Windows 8 和 [Windows server 2012 相容性操作手冊](https://www.microsoft.com/download/details.aspx?id=27416) 。 未來的 Windows 版本將移除 RDS 用戶端元件。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該遷移至 [WCF 資料服務](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="syntax"></a>語法  
  
```  
  
DataControl.Refresh  
```  
  
#### <a name="parameters"></a>參數  
 *DataControl*  
 代表 RDS 的物件變數 [。DataControl](./datacontrol-object-rds.md) 物件。  
  
## <a name="remarks"></a>備註  
 使用**Refresh**方法之前，您必須先設定[Connect](./connect-property-rds.md)、 [Server](./server-property-rds.md)和[SQL](./sql-property.md)屬性。 與 RDS 相關聯之表單上的所有資料繫結控制項 **。DataControl** 物件將會反映一組新的記錄。 任何預先存在的 [記錄集](../ado-api/recordset-object-ado.md) 物件都會釋出，並捨棄任何未儲存的變更。 **Refresh**方法會自動讓第一個記錄成為目前的記錄。  
  
 當您處理資料時，最好定期呼叫 **Refresh** 方法。 如果您在一段時間內取出資料，然後將其保留在用戶端電腦上，則可能會過期。 您所做的任何變更都可能會失敗，因為其他人可能會在您之前變更記錄並提交變更。  
  
## <a name="applies-to"></a>套用至  
 [DataControl 物件 (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>另請參閱  
 [Refresh 方法範例 (VB) ](../ado-api/refresh-method-example-vb.md)   
 [ (VBScript) 的 Refresh 方法範例 ](./refresh-method-example-vbscript.md)   
 [通訊錄命令按鈕](../../guide/remote-data-service/address-book-command-buttons.md)   
 [RDS)  (CancelUpdate 方法 ](./cancelupdate-method-rds.md)   
 [ (ADO) 的 Refresh 方法 ](../ado-api/refresh-method-ado.md)   
 [SubmitChanges 方法 (RDS)](./submitchanges-method-rds.md)