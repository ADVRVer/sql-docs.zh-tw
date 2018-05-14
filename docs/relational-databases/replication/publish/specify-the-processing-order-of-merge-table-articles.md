---
title: 指定合併資料表發行項的處理順序 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], processing order
- merge replication [SQL Server replication], article processing order
ms.assetid: 9fe576a2-f5fb-4fdf-bd7d-cb322021b669
caps.latest.revision: 33
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6d0a1519c85e1b398fc4be3491b680997cac01b5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="specify-the-processing-order-of-merge-table-articles"></a>指定合併資料表發行項的處理順序
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  合併式複寫可讓您指定在同步處理期間，合併代理程式處理發行項的順序。 當您使用複寫預存程序建立發行項時，可以透過程式設計方式對每一個發行項指派順序。 發行項會依照從最低值到最高值的順序來處理。 如果兩個發行項有相同的值，就會同時處理它們。 如需詳細資訊，請參閱[指定合併發行項的處理順序](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)。  
  
### <a name="to-specify-the-processing-order-for-a-new-merge-article"></a>為新的合併發行項指定處理順序  
  
1.  在發行集資料庫的發行者端，執行 [sp_addmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)。 針對 **@processing_order**。 如需詳細資訊，請參閱 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)。  
  
    > [!NOTE]  
    >  當建立排序的發行項時，您應該在發行項順序值之間留一些間距。 這樣可讓您在將來更容易設定新的值。 例如，如果您有三個發行項需要指定固定的處理順序，請分別將 **@processing_order** 的值設定為 10、20 和 30，而不是 1、2 和 3。  
  
### <a name="to-change-the-processing-order-of-a-merge-article"></a>變更合併發行項的處理順序  
  
1.  若要決定發行項的處理順序，請執行 [sp_helpmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)，並記下結果集中的 **processing_order** 值。  
  
2.  在發行集資料庫的發行者端，執行 [sp_changemergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)。 針對 **processing_order** 指定 **@property** 的值，並針對 **@value**。  
  
## <a name="see-also"></a>另請參閱  
 [指定合併發行項的處理順序](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)  
  
  
