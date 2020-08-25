---
description: SortDirection 屬性 (RDS)
title: SortDirection 屬性 (RDS) |Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SortDirection property [RDS]
ms.assetid: 1d9d8715-e4ad-4ff3-bf7f-f1dc0532d8c2
author: rothja
ms.author: jroth
ms.openlocfilehash: a7a8aca2bb5dd4acf6a2b7b2702eb7807d520f73
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "88767467"
---
# <a name="sortdirection-property-rds"></a>SortDirection 屬性 (RDS)
指出排序次序為遞增或遞減。  
  
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，Windows 作業系統中不再包含 RDS 伺服器元件 (如需詳細) 資訊，請參閱 Windows 8 和 [Windows server 2012 相容性操作手冊](https://www.microsoft.com/download/details.aspx?id=27416) 。 未來的 Windows 版本將移除 RDS 用戶端元件。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該遷移至 [WCF 資料服務](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="syntax"></a>語法  
  
```  
  
DataControl.SortDirection = value  
```  
  
#### <a name="parameters"></a>參數  
 *DataControl*  
 代表 RDS 的物件變數 [。DataControl](./datacontrol-object-rds.md) 物件。  
  
 *值*  
 **布林**值，當設為**True**時，表示排序方向為遞增。 **False** 表示遞減順序。  
  
## <a name="remarks"></a>備註  
 [SortColumn](./sortcolumn-property-rds.md)、 **SortDirection**、 [FilterValue](./filtervalue-property-rds.md)、 [FilterCriterion](./filtercriterion-property-rds.md)和[FilterColumn](./filtercolumn-property-rds.md)屬性提供用戶端快取上的排序和篩選功能。 排序功能會使用一個資料行的值來排序記錄。 篩選功能會根據尋找準則顯示記錄的子集，而完整的 [記錄集會](../ado-api/recordset-object-ado.md) 保留在快取中。 [Reset](./reset-method-rds.md)方法會執行準則，並將目前的**記錄集**取代為可更新的**記錄集**。  
  
## <a name="applies-to"></a>套用至  
 [DataControl 物件 (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>另請參閱  
 [FilterColumn、FilterCriterion、FilterValue、SortColumn 和 SortDirection 屬性以及 Reset 方法範例 (VBScript) ](./filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Sort 屬性](../ado-api/sort-property.md)   
 [SortColumn 屬性 (RDS)](./sortcolumn-property-rds.md)