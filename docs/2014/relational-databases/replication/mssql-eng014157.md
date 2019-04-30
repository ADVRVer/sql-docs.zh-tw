---
title: MSSQL_ENG014157 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014157 error
ms.assetid: 1a0890cf-d977-43e0-a2ba-9c5ff1a8f856
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 26befe89debb6fd890abeee9ea258e53a028b50c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63191498"
---
# <a name="mssqleng014157"></a>MSSQL_ENG014157
    
## <a name="message-details"></a>訊息詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|14157|  
|事件來源|MSSQLSERVER|  
|元件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符號名稱||  
|訊息文字|由訂閱者 '%s' 建立給發行集 '%s' 的訂閱已經過期且已經卸除。|  
  
## <a name="explanation"></a>說明  
 「訂閱者」必須在發行集保留期限中指定的時間內與「發行者」同步。 如果「訂閱者」未於這個期限內同步，訂閱便會過期。 如需詳細資訊，請參閱 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)。  
  
## <a name="user-action"></a>使用者動作  
 訂閱必須重新建立和初始化，「訂閱者」才能再次開始接收資料變更：  
  
-   如需建立訂閱的資訊，請參閱[訂閱發行集](subscribe-to-publications.md)。  
  
-   如需初始化訂閱的詳細資訊，請參閱[初始化訂閱](initialize-a-subscription.md)。  
  
 如果訂閱資料庫包含尚未與「發行者」同步的變更，您可以使用 [tablediff Utility](../../tools/tablediff-utility.md) 判斷發行集和訂閱資料庫中不同的資料列。  
  
 您可以建立發行集保留期限，以避免訂閱過期。 請小心設定最大值，因為這個值可能導致儲存更多資料和中繼資料，結果影響效能。 如需詳細資訊，請參閱 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤和事件參考 &#40;複寫&#41;](errors-and-events-reference-replication.md)  
  
  
