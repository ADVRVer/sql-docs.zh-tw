---
title: 資料流屬性 |Microsoft 文件
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADOStreamConstruction::GetStream
- ADOStreamConstruction::PutStream
- ADOStreamConstruction::put_Stream
- ADOStreamConstruction::Stream
- ADOStreamConstruction::get_Stream
helpviewer_keywords:
- Stream property
ms.assetid: 4a44f9f6-0265-4c00-8def-d85b6af923b1
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dd848306588cba57a25e0a8e7e8a45ab5c563766
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="stream-property"></a>資料流內容
取得或設定 OLE DB**資料流**物件上從 / **ADOStreamConstruction**物件。  
  
 讀取/寫入  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT get_Stream([out, retval] IUnknown** ppStream);  
HRESULT put_Stream([in] IUnknown* pStream);  
```  
  
## <a name="parameters"></a>參數  
 *ppStream*  
 OLE DB 指標**資料流**物件。  
  
 *pStream*  
 OLE DB**資料流**物件。  
  
## <a name="return-values"></a>傳回值  
 這個屬性的方法會傳回標準的 HRESULT 值。 這包括 S_OK 以及 E_FAIL。  
  
## <a name="applies-to"></a>適用於  
 [ADOStreamConstruction 介面](../../../ado/reference/ado-api/adostreamconstruction-interface.md)
