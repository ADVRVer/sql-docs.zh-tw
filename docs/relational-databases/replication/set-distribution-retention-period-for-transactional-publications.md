---
title: "設定交易式發行集的散發保留週期 | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
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
- transaction retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: 9a98c53a-fea5-4235-b23d-6c69587c5676
caps.latest.revision: "37"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eb6f7ddde1dfb0546446bd4c0caee1075f182413
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="set-distribution-retention-period-for-transactional-publications"></a>設定交易式發行集的散發保留週期
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] 在 [散發資料庫屬性 - \<散發資料庫>] 對話方塊中，指定最短和最長散發保留期限。 這可以從 [散發者屬性 - \<散發者>] 對話方塊的 [一般] 頁面取得。 如需存取此對話方塊的詳細資訊，請參閱[檢視及修改散發者和發行者屬性](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)。  
  
### <a name="to-specify-the-distribution-retention-period"></a>若要指定散發保留期限  
  
1.  在 [散發者屬性 - \<散發者>] 對話方塊的 [一般] 頁面上，按一下散發資料庫的屬性按鈕 (**…**)。  
  
2.  若要指定最短散發保留期限，請在 **[至少]** 方塊中輸入值；若要指定最長散發期限，請在 **[但是不能超過]** 方塊中輸入值。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [設定散發](../../relational-databases/replication/configure-distribution.md)   
 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
