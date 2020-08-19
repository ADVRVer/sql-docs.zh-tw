---
description: RowPosition 屬性 (ADO)
title: " (ADO) 的 RowPosition 屬性 |Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction::put_RowPosition
- ADORecordConstruction::PutRowPosition
- ADORecordConstruction::GetRowPosition
- ADORecordConstruction::RowPosition
- ADORecordConstruction::get_RowPosition
helpviewer_keywords:
- RowPosition property [ADO]
ms.assetid: 9d068fed-39bf-4842-afc3-686a2af2145d
author: rothja
ms.author: jroth
ms.openlocfilehash: 330c090c9e4eedd6a083d58a55243d470514541f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442460"
---
# <a name="rowposition-property-ado"></a>RowPosition 屬性 (ADO)
取得或設定來自**ADORecordsetConstruction**物件的 OLE DB **RowPosition**物件。 當您使用 **put_RowPosition** 設定 **RowPosition** 物件時，產生的 **記錄集** 物件會使用 **RowPosition** 物件來決定目前的資料列。  
  
 讀取/寫入  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT get_RowPosition([out, retval] IUnknown** ppRowPos);  
HRESULT put_RowPosition([in] IUnknown* pRowPos);  
```  
  
## <a name="parameters"></a>參數  
 *ppRowPos*  
 OLE DB **RowPosition** 物件的指標。  
  
 *PRowPos*  
 OLE DB **RowPosition** 物件。  
  
## <a name="return-values"></a>傳回值  
 這個屬性方法會傳回標準的 HRESULT 值，包括 S_OK 和 E_FAIL。  
  
## <a name="remarks"></a>備註  
 當設定這個屬性時，如果**RowPosition**物件上的資料列**集**物件與**記錄集**物件**上的資料列集物件不同**，前者會覆寫後者。 相同的行為也適用于**RowPosition**的目前**章節**。  
  
## <a name="applies-to"></a>套用至  
 [ADORecordsetConstruction 介面](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
