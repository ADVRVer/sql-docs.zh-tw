---
title: SortColumn 屬性 (RDS) |Microsoft 文件
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: drivers
ms.component: reference
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SortColumn property [RDS]
ms.assetid: f6f80f67-f0fb-4e63-a5f5-8fdf312aac63
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f166971df317045b04e644377c27c3cf71c3cd41
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="sortcolumn-property-rds"></a>SortColumn 屬性 (RDS)
指出哪些資料行來排序記錄。  
  
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，RDS 伺服器元件已不再包含在 Windows 作業系統中 (請參閱 < Windows 8 和[Windows Server 2012 相容性手冊](https://www.microsoft.com/en-us/download/details.aspx?id=27416)如需詳細資訊)。 Windows 的未來版本將移除 RDS 用戶端元件。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該移轉到[WCF 資料服務](http://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="syntax"></a>語法  
  
```  
  
DataControl.SortColumn = String  
```  
  
#### <a name="parameters"></a>參數  
 *DataControl*  
 物件變數，表示[.RDSDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)物件。  
  
 *字串*  
 A**字串**值，表示用來排序資料錄的資料行別名的名稱。  
  
## <a name="remarks"></a>備註  
 **SortColumn**， [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md)， [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md)， [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md)，和[FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)屬性會提供排序和篩選功能，用戶端快取。 排序功能的訂單記錄中有一個資料行的值。 篩選功能會顯示在完整的尋找準則的所有記錄的子集[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)維護快取中。 [重設](../../../ado/reference/rds-api/reset-method-rds.md)方法會執行準則和取代目前**資料錄集**具有可更新**資料錄集**。  
  
 若要排序依據**資料錄集**，您必須先儲存任何暫止的變更。 如果您使用**.RDSDataControl**，您可以使用[SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md)方法。 例如，如果您**.RDSDataControl**是名為 ADC1，您的程式碼會是`ADC1.SubmitChanges`。 如果您使用 ADO**資料錄集**，您可以使用其[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)方法。 使用**UpdateBatch**是建議的方法**資料錄集**建立的物件[CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md)方法。 例如，您的程式碼可能是`myRS.UpdateBatch`或`ADC1.Recordset.UpdateBatch`。  
  
## <a name="applies-to"></a>適用於  
 [DataControl 物件 (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>另請參閱  
 [FilterColumn、 FilterCriterion、 FilterValue、 SortColumn，和 SortDirection 屬性及重設方法範例 (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [排序內容](../../../ado/reference/ado-api/sort-property.md)   
 [SortDirection 屬性 (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)





