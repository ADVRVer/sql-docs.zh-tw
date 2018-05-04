---
title: InvokeService (RDS) |Microsoft 文件
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- InvokeService [RDS]
ms.assetid: ad45c676-ec7e-4a3a-9a6b-a54f75eb3012
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a78c815f75b5e30713e0b7f9e5b7ec83c4c3eb6d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="invokeservice-rds"></a>InvokeService (RDS)
傳回所要求介面的指標上更適用的版本的物件。  
  
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，RDS 伺服器元件已不再包含在 Windows 作業系統中 (請參閱 < Windows 8 和[Windows Server 2012 相容性手冊](https://www.microsoft.com/en-us/download/details.aspx?id=27416)如需詳細資訊)。 Windows 的未來版本將移除 RDS 用戶端元件。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該移轉到[WCF 資料服務](http://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="syntax"></a>語法  
  
```  
  
object.InvokeService(REFID riid, IUknown* punkNotSoFunctionalInterface, IUknown** ppunkMoreFunctionalInterface) As HRESULT  
```  
  
#### <a name="parameters"></a>參數  
 *riid*  
  
 [in]所要求介面的識別項。  
  
 *punkNotSoFunctionalInterface*  
  
 [in]較不支援的來源物件。  
  
 *ppunkMoreFunctionalInterface*  
  
 [out]接收要求中的介面指標的指標變數的位址*riid*。 成功傳回時， *ppunkMoreFunctionalInterface*參數包含物件的要求的介面指標。 如果物件不支援指定的介面*riid*， *ppunkMoreFunctionalInterface*設為 NULL。  
  
## <a name="return-value"></a>傳回值  
 HRESULT 值，指出呼叫**InvokeService**方法是否成功。  
  
## <a name="remarks"></a>備註  
 RDS 資料指標引擎實作**InvokeService**會輸入資料列集 （或多個結果物件），會填入資料指標引擎，從輸入資料列集，並傳回指標本身。  
  
## <a name="applies-to"></a>適用於  
 [IRDSService 介面 (RDS)](../../../ado/reference/rds-api/irdsservice-interface-rds.md)  
  
## <a name="see-also"></a>另請參閱  
 [RDS 方法](../../../ado/reference/rds-api/rds-methods.md)


