---
title: 傳送結果集至伺服器 （擴充預存程序 API） |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
author: rothja
ms.author: jroth
ms.openlocfilehash: 7121626f3de850c670f160a945ba3de8533cd7ee
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064296"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>將結果集傳送到伺服器 (擴充預存程序 API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 請改用 CLR 整合。  
  
 傳送結果集時[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，擴充預存程序應該呼叫適當的 API，如下所示：  
  
-   **Srv_sendmsg**之前或之後與已傳送所有資料列 （如果有的話），可能會以任何順序呼叫函式**srv_sendrow**。 所有訊息必須都傳送至用戶端，以都傳送完成狀態之前**srv_senddone**。  
  
-   系統會針對傳送到用戶端的每個資料列，呼叫 **srv_sendrow** 函式一次。 所有資料列必須傳送至用戶端之前任何訊息、 狀態值或完成狀態會傳送**srv_sendmsg**，則**srv_status**引數**srv_pfield**，或**srv_senddone**。  
  
-   尚未定義其資料行的資料列傳送**srv_describe**導致應用程式引發參考用錯誤訊息，並傳回給用戶端失敗。 在此情況下，不會傳送資料列。  
  
## <a name="see-also"></a>另請參閱  
 [建立擴充預存程序](../../relational-databases/extended-stored-procedures-programming/creating-extended-stored-procedures.md)  
  
  
