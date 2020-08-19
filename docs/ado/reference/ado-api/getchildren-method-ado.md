---
description: GetChildren 方法 (ADO)
title: " (ADO) 的 GetChildren 方法 |Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_GetChildren
- _Record::GetChildren
helpviewer_keywords:
- GetChildren method [ADO]
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
author: rothja
ms.author: jroth
ms.openlocfilehash: 906c20d19143f4f1e8fe0b6c1e91585893acfa5d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443580"
---
# <a name="getchildren-method-ado"></a>GetChildren 方法 (ADO)
傳回 [記錄集](../../../ado/reference/ado-api/recordset-object-ado.md) ，其資料列代表集合 [記錄](../../../ado/reference/ado-api/record-object-ado.md)的子系。  
  
## <a name="syntax"></a>語法  
  
```  
  
Set recordset = record.GetChildren  
```  
  
## <a name="return-value"></a>傳回值  
 **記錄集**物件，其中每個資料列都代表目前**記錄**物件的子系。 例如，代表目錄之 **記錄** 的子系會是包含在上層目錄中的檔案和子目錄。  
  
## <a name="remarks"></a>備註  
 此提供者會決定哪些資料行存在於傳回的 **記錄集中**。 例如，檔來源提供者一律會傳回資源 **記錄集**。  
  
## <a name="applies-to"></a>套用至  

:::row:::
    :::column:::
        [Record 物件 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
    :::column-end:::
    :::column:::
        [Recordset 物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
    :::column-end:::
:::row-end:::
