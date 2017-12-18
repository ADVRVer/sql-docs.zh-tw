---
title: "以 COM 為基礎的自訂解析程式 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM-based resolvers [SQL Server replication]
- custom resolvers [SQL Server replication]
ms.assetid: 94195797-ad7a-4962-a8e3-b259cd13aa38
caps.latest.revision: "36"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 389e7b9b83ee1f9dda06e8338f9b4c7b34f18a12
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="advanced-merge-replication-conflict---com-based-custom-resolvers"></a>進階合併式複寫衝突 - 以 COM 為基礎的自訂解析程式
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] 自訂解決器比預設解決機制更具有彈性，它們能使用複寫資料實作應用程式要求的商務邏輯。 以 COM 為基礎的自訂解決器是一個實作 **ICustomResolver** COM 介面、其方法與屬性，以及特別為衝突解決所設計的其他支援介面與類型定義之動態連結程式庫 (DLL)。  
  
> [!NOTE]  
>  如有可能，建議使用商務邏輯處理常式，而不要使用以 COM 為基礎的自訂解決器。 如需商務邏輯處理常式的詳細資訊，請參閱[合併同步處理期間執行商務邏輯](../../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)。  
  
 若要建立自訂 COM 解決器，您可以使用 replrec.dll 中所提供的類型程式庫；依預設，此程式庫安裝在 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM。  
  
 在撰寫自訂 COM 解決器之前，您必須先決定：  
  
-   您想解決的資料列變更之類型 (例如更新、插入、刪除)，以及在合併變更的上傳、下載，或兩者兼具期間，是否應叫用解決器。 您可以指定一類變更、所有變更，或者任意組合。 預設的合併衝突解決器可處理自訂解決器未能涵蓋的任何衝突。  
  
-   解決衝突時是否要使用資料行追蹤。 若啟用資料行層級追蹤，只有衝突所在的資料行中的資料會加上旗標標示為衝突，否則這些資料便會遭到合併。 但是，衝突解決的方式與資料列層級追蹤相同：優先權勝利者會覆寫整列資料 (但這些資料可能是來自於「發行者」、「訂閱者」的混合值或一些非來自「發行者」亦非「訂閱者」的變更值)。 如需相關資訊，請參閱 [Detect and Resolve Merge Replication Conflicts](../../../relational-databases/replication/merge/advanced-merge-replication-resolve-merge-replication-conflicts.md)。  
  
 若要實作以 COM 為基礎的自訂 Conflict Resolver，請參閱＜ [Implement a Custom Conflict Resolver for a Merge Article](../../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)＞。  
  
 自訂解決器是指定給發行項的，而不是指定給整個發行集的。 同一個解決器可以用於多個發行項，但是自訂解決器的邏輯通常為特定資料表所特有。 如果在建立解決器之後修改用於發行項的資料表 (例如，重新命名用於衝突解決的資料行)，則自訂解決器可能需要修改及重新編譯。  
  
 若要指定自訂解析程式，請參閱＜ [Specify a Merge Article Resolver](../../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)＞。  
  
## <a name="see-also"></a>另請參閱  
 [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Microsoft COM-Based Resolvers](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-com-based-resolvers.md)  
  
  
