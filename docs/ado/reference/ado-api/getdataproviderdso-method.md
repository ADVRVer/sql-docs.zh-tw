---
title: "GetDataProviderDSO 方法 |Microsoft 文件"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GetDataProviderDSO Method [ADO]
ms.assetid: 5a4c6bd5-0c79-4f81-a977-0561392d8d50
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 90c18a4c83f556d4283b76c364686e8308d75474
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="getdataproviderdso-method"></a>GetDataProviderDSO 方法
從 Shape 提供者擷取基礎 OLE DB 資料來源物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
HRESULT GetDataProviderDSO(  
      IUnknown **ppDataProviderDSOIUnknown  
);  
```  
  
#### <a name="parameters"></a>參數  
 *ppDataProviderDSOIUnknown*  
 [out] 傳回基礎 OLE DB 資料來源物件的 IUnknown 指標的指標。  
  
## <a name="remarks"></a>備註  
 這個方法就不 addref 介面指標。 如果呼叫端計劃將指標，呼叫端必須執行必要的 addref 和 release。  
  
## <a name="applies-to"></a>適用對象  
 [IDSOShapeExtensions 介面](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
