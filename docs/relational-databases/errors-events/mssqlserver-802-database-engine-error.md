---
title: "MSSQLSERVER_802 - Database Engine 錯誤 | Microsoft Docs"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 802 (Database Engine error)
ms.assetid: 5892ed24-4dcb-4bf9-a8a4-a7ca898832d5
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 83a4a02b0977f3a1b9feec0ad720aef6728cb906
ms.contentlocale: zh-tw
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver802---database-engine-error"></a>MSSQLSERVER_802 - Database Engine 錯誤
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|802|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|NO_BUFS|  
|訊息文字|緩衝集區裡沒有足夠的可用記憶體。|  
  
## <a name="explanation"></a>說明  
當緩衝集區已滿，而且緩衝集區已經無法成長時，就會造成這個錯誤。  
  
## <a name="user-action"></a>使用者動作  
下列清單概述有助於疑難排解記憶體錯誤的一般步驟：  
  
1.  確認是否有其他應用程式或服務正在耗用此伺服器的記憶體。 重新設定比較不重要的應用程式或服務，以降低其記憶體耗用量。  
  
2.  開始收集 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Buffer Manager** 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Memory Manager** 的效能監視器計數器。  
  
3.  檢查下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記憶體組態參數：  
  
    -   **max server memory**  
  
    -   **min server memory**  
  
    -   **min memory per query**  
  
    注意任何不尋常的設定，並視需要加以更正。 說明 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的增加記憶體需求。 預設值列於《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜設定伺服器組態選項＞。  
  
4.  當您看到這些錯誤訊息時，請觀察 DBCC MEMORYSTATUS 輸出以及它變更的方式。  
  
5.  檢查工作負載 (並行工作階段的數目以及目前正在執行的查詢數)。  
  
下列動作可以為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供更多可用的記憶體：  
  
-   如果有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外的應用程式正在耗用資源，請嘗試停止這些應用程式或在不同的伺服器上執行這些應用程式。  
  
-   如果已經設定 **max server memory**，請增加其設定值。  
  
執行下列 DBCC 命令，以便釋放數個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記憶體快取。  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
如果仍繼續發生該問題，您必須進一步研究，而且可能必須降低工作負載。  
  

