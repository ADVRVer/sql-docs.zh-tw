---
title: "srv_setcoldata (擴充預存程序 API) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8be41b91658e1eeb2b5da1c361d64b76829e6126
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="srvsetcoldata-extended-stored-procedure-api"></a>srv_setcoldata (擴充預存程序 API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
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
  
## <a name="returns"></a>傳回值  
 SUCCEED 或 FAIL。  
  
## <a name="remarks"></a>備註  
 資料列的每個資料行必須先用 **srv_describe** 定義。 資料行資料位址最初是以 **srv_describe** 設定。 如果資料行資料的位址變更，則必須呼叫 **srv_setcoldata** 來指定資料的新位址，而且必須針對每一個變更的資料行個別呼叫 **srv_setcoldata**。  
  
 Null 資料的表示方式是使用 **srv_setcollen** 將資料行的長度設定為 0。 然後會忽略資料位址。  
  
> [!IMPORTANT]  
>  您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。 如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)。  
  
## <a name="see-also"></a>另請參閱  
 [srv_describe &#40;擴充預存程序 API&#41;](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)  
  
  
