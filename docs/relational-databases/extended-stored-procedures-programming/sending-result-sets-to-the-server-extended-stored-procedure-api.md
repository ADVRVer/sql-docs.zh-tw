---
title: "傳送到伺服器 （擴充預存程序 API） 的結果集 |Microsoft 文件"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 37eb992a4ef260b1d8b94991e95fae6e9326bd6f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>將結果集傳送到伺服器 (擴充預存程序 API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 請改用 CLR 整合。  
  
 傳送結果集時[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，擴充預存程序應該呼叫適當的 API，如下所示：  
  
-   **Srv_sendmsg**之前或之後與已傳送所有資料列 （如果有的話），可能依任何順序呼叫函式**srv_sendrow**。 所有訊息必須都傳送至用戶端，以都傳送完成狀態之前**srv_senddone**。  
  
-   **Srv_sendrow**每個資料列給用戶端傳送一次呼叫函式。 所有資料列必須只能傳送到用戶端之前任何訊息、 狀態值或完成狀態才會傳送**srv_sendmsg**、 **srv_status**引數的**srv_pfield**，或**srv_senddone**。  
  
-   未定義的所有資料行的資料列傳送**srv_describe**導致應用程式引發參考用錯誤訊息，並傳回給用戶端失敗。 在此情況下，不會傳送資料列。  
  
## <a name="see-also"></a>請參閱＜  
 [建立擴充預存程序](../../relational-databases/extended-stored-procedures-programming/creating-extended-stored-procedures.md)  
  
  
