---
title: 資料庫已取代的維護計畫 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- suspended database maintenance plans
- database maintenance plans [SQL Server Agent]
- maintenance plans [SQL Server Agent]
ms.assetid: efac127c-6c81-4c7a-a6c4-9aae5d15545d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7d41763582632a92b3a38bdbd67ee55b65f95b6d
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66095754"
---
# <a name="database-maintenance-plans-superseded"></a>已取代資料庫維護計畫
    
## <a name="component"></a>元件  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>描述  
 現有的資料庫維護計劃已經升級，而且仍會繼續運作。 但是，您將無法使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來建立新的資料庫維護計劃。 若要在 [物件總管] 中檢視維護計畫，請展開 [管理]，然後再展開 [舊版]。 您也可以選取新的格式來移轉現有的資料庫維護計畫**移轉**從內容功能表中的任何資料庫維護計畫。 因為新維護計畫功能並非直接取代資料庫維護計畫，所以移轉後，某些功能可能會遺失。 移轉資料庫維護計畫並不會刪除舊計畫，所以您可以測試維護計畫的功能後，再移除舊計畫。  
  
 資料庫維護計畫不再支援下列功能：  
  
-   記錄傳送  
  
-   **嘗試修復所有次要問題**選項**資料庫完整性檢查**工作  
  
## <a name="corrective-action"></a>更正動作  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 禁止在資料庫維護計劃中包含記錄傳送。 如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜記錄傳送＞。  
  
  
