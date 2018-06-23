---
title: 發行集屬性、一般 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.newpubwizard.pubproperties.general.f1
ms.assetid: 7912362f-c4d6-4f60-bd39-dee1f656ed18
caps.latest.revision: 24
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6b9659f1f60265072c5bdf5d5ca0a57364894277
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36023079"
---
# <a name="publication-properties-general"></a>發行集屬性，一般
  **[發行集屬性]** 對話方塊的 **[一般]** 頁面，包含發行集的基本資訊，例如名稱、描述和訂閱到期原則。  
  
## <a name="options"></a>選項。  
 **名稱**  
 發行集的名稱 (唯讀)。  
  
 **[資料庫備份]**  
 發行集資料庫的名稱 (唯讀)。  
  
 **說明**  
 發行集的描述。  
  
 **型別**  
 發行集的類型 (唯讀)。  
  
 **訂閱過期**  
 選取訂閱過期的選項之一： **[訂閱永遠不會過期]** 或 **[訂閱會過期]**，並提供明確的時間週期 (**[間隔]**)。  
  
 針對快照式發行集和交易式發行集， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 建議您接受預設的 **[訂閱永遠不會過期]** 設定。  
  
 針對合併式複寫， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 建議您接受預設的 **[訂閱會過期]** 設定，並將 **[間隔]** 儘可能設成較低的值。 隨著訂閱過期週期長度的增加，儲存的中繼資料量也會跟著增加，因而可能影響效能。 請在中斷訂閱者的連接或長時間不進行同步處理，以及儲存和處理大量中繼資料可能造成的效能問題之間，進行評估以取得平衡點。  
  
 如需詳細資訊，請參閱＜ [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)＞。  
  
 **相容性層級**  
 僅限[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本，而且僅限合併式發行集。 選取與此發行集同步處理之訂閱者所需的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 最低版本。 決定相容性層級的相關規則有數個。  
  
## <a name="see-also"></a>另請參閱  
 [Create a Publication](publish/create-a-publication.md)   
 [檢視及修改發行集屬性](publish/view-and-modify-publication-properties.md)   
 [發行資料和資料庫物件](publish/publish-data-and-database-objects.md)  
  
  