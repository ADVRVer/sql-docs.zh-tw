---
title: 篩選設定 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.filtersettings.f1
ms.assetid: 1b401d7d-db8a-4ba1-acb1-b8dec14e3311
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d9ceca85c8f0f09137d0ed82730a4f409114369
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68128116"
---
# <a name="filter-settings"></a>篩選設定
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[篩選設定]** 對話方塊可讓您針對「複寫監視器」中的方格定義篩選。 例如，若只要顯示在 **[所有訂閱]** 索引標籤中處於使用中狀態的訂閱，請依序選取 **[資料行名稱]** 資料行中的 **[狀態]** 、 **[運算子]** 資料行中的 **[等於]** ，以及 **[值1]** 資料行中的 **[使用中]** 。 在您定義以一個或多個資料行為基礎的篩選之後，系統便套用此篩選，如此方格就只會顯示符合篩選準則的資料列子集。  
  
## <a name="options"></a>選項。  
 **[狀態]**  
 選取您想要用來篩選的資料行名稱。 您可以讓篩選以一個或多個資料行為基礎。  
  
 **[等於]**  
 選取篩選的運算子，例如 **[小於或等於]** 。  
  
 **值1** 和 **值2**  
 輸入或選取篩選的值。 大部分運算子只需要 **[值1]** 資料行的值，但 **[介於]** 和 **[不介於]** 運算子則需要 **[值2]** 資料行的值。  
  
 **清除篩選**  
 按一下此按鈕即可清除已定義的所有篩選。 若要移除單一篩選，請選取篩選資料列並按下 Delete 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [監視複寫](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
