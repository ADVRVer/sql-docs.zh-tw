---
title: srv_setcoldata (擴充預存程序 API) | Microsoft Docs
description: 瞭解擴充預存程式 API 中 srv_setcoldata 會指定資料行的目前位址。
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_setcoldata
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_setcoldata
ms.assetid: 2e19205a-25ca-4d4a-916b-d591cf2c892b
author: rothja
ms.author: jroth
ms.openlocfilehash: 3c9d151ca52e52d550d7eba42cb6e53af1d8417e
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248212"
---
# <a name="srv_setcoldata-extended-stored-procedure-api"></a>srv_setcoldata (擴充預存程序 API)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 請改用 CLR 整合。  
  
 指定資料行資料的目前位址。  
  
## <a name="syntax"></a>語法  
  
```  
  
int srv_setcoldata (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
void *  
data   
);  
```  
  
## <a name="arguments"></a>引數  
 *srvproc*  
 是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼。 擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。  
  
 *column*  
 表示指定位址之目標資料行的編號。 資料行的編號會從 1 開始。  
  
 *data*  
 這是資料行資料的指標。 配置給 *data* 的記憶體要等到另一個 **srv_setcoldata** 呼叫取代資料行資料或是呼叫 **srv_senddone** 之後，才能釋放。  
  
## <a name="returns"></a>傳回  
 SUCCEED 或 FAIL。  
  
## <a name="remarks"></a>備註  
 資料列的每個資料行必須先用 **srv_describe** 定義。 資料行資料位址最初是以 **srv_describe** 設定。 如果資料行資料的位址變更，則必須呼叫 **srv_setcoldata** 來指定資料的新位址，而且必須針對每一個變更的資料行個別呼叫 **srv_setcoldata**。  
  
 Null 資料的表示方式是使用 **srv_setcollen** 將資料行的長度設定為 0。 然後會忽略資料位址。  
  
> [!IMPORTANT]  
>  您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。 如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。  
  
## <a name="see-also"></a>另請參閱  
 [srv_describe &#40;擴充預存程序 API&#41;](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)  
  
  
