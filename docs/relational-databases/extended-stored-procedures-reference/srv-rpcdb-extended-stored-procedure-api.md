---
title: "srv_rpcdb (擴充預存程序 API) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: srv_rpcdb
apilocation: opends60.dll
apitype: DLLExport
dev_langs: C++
helpviewer_keywords: srv_rpcdb
ms.assetid: d52bfd22-7a7c-4ab0-af65-df96ff359e6f
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5228cb286ff9862568b05275d9ab499fe152f924
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="srvrpcdb-extended-stored-procedure-api"></a>srv_rpcdb (擴充預存程序 API)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 請改用 CLR 整合。  
  
 傳回目前遠端預存程序的資料庫名稱元件。  
  
## <a name="syntax"></a>語法  
  
```  
  
DBCHAR * srv_rpcdb (  
SRV_PROC * srvproc,int *len );  
```  
  
## <a name="arguments"></a>引數  
 *srvproc*  
 是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼。 擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。  
  
 *len*  
 這是 **int** 變數的指標，此變數會接收資料庫名稱的長度。 如果 *len* 為 NULL，則不會傳回資料庫名稱的長度。  
  
## <a name="returns"></a>傳回值  
 目前遠端預存程序的資料庫名稱部分以 null 結尾字串的 DBCHAR 指標。 如果沒有目前遠端預存程序，則會傳回 NULL 且 *len* 參數設定為 - 1。  
  
## <a name="remarks"></a>備註  
 函數只會傳回遠端預存程序物件名稱的資料庫元件。 其中不包含擁有人、遠端預存程序名稱和遠端預存程序號碼的選擇性規範。  
  
> [!IMPORTANT]  
>  您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。 如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)。  
  
  
