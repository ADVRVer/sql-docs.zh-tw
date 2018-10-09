---
title: srv_got_attention (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- srv_got_attention
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_got_attention
ms.assetid: 805e68e1-d17f-41bd-8b9f-a27283bb6fbe
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: cc6c05c84513766a5597dc31bc7e2495c90ecc7b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48097138"
---
# <a name="srvgotattention-extended-stored-procedure-api"></a>srv_got_attention (擴充預存程序 API)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 請改用 CLR 整合。  
  
 檢查是否需要中止目前的連接或工作，並在連接遭到清除或批次遭到中止時傳回 TRUE  
  
## <a name="syntax"></a>語法  
  
```  
  
BOOL srv_got_attention  
(SRV_PROC *  
srvproc  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 *srvproc*  
 識別資料庫連接的指標。  
  
## <a name="return-value"></a>傳回值  
 如果連接遭到清除或批次遭到中止，則為 TRUE。 如果連接或批次作用中，則為 FALSE。  
  
## <a name="remarks"></a>備註  
 長時間執行的擴充預存程序應該透過定期呼叫 **srv_got_attention** 來檢查伺服器的注意事項，讓該程序可以在連線到終止或批次遭到中止時自行結束。  
  
> [!IMPORTANT]  
>  您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。 如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)。  
  
  
