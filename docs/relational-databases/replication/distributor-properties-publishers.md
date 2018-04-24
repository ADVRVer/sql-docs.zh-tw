---
title: 散發者屬性、發行者 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.rep.configdistwizard.distproperties.publishers.f1
helpviewer_keywords:
- Distributor Properties dialog box
ms.assetid: 31c81898-11ca-4d2f-afea-2fbc71e19ce4
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5975fe4d456175f2351b9f308acc383f23490d32
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="distributor-properties-publishers"></a>散發者屬性，發行者
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[散發者屬性]** 對話方塊的 **[發行者]** 頁面可讓您啟用發行者，以使用此散發者。 您也可以設定與這些發行者相關聯的屬性。 請注意，讓發行者可以使用這個伺服器作為它的遠端散發者，並不會使該伺服器成為發行者。 您必須連接到發行者，設定其發行，並選擇此伺服器為散發者。 您可以透過新增發行集精靈來設定發行者和選擇散發者。  
  
## <a name="options"></a>選項。  
 **發行者**  
 選取可使用這個散發者的伺服器。 按一下發行者旁的 [屬性] 按鈕 **(...)** ，以檢視和設定其他屬性。  
  
 **[加入]**  
 如果未列出您要允許的伺服器，請按一下 **[加入]** ，將 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 發行者或 Oracle 發行者加入可用發行者的清單中。 如果您加入的伺服器是第一部使用此散發者作為遠端散發者的伺服器，系統會提示您提供管理連結密碼。  
  
 **管理連結密碼**  
 使用 **distributor_admin** 登入進行發行者和遠端散發者的連接複寫時，這可用來指定或更新該連接複寫的密碼：  
  
-   如果散發者伺服器只是當成本機散發者，這個密碼會隨機產生並自動設定。  
  
-   如果散發者已經有遠端發行者，此頁面上或設定散發精靈的 **[散發者密碼]** 頁面上一開始就會提供密碼。  
  
-   如果啟用此散發者的第一個遠端發行者，系統會提示您輸入密碼。  
  
 如需散發者安全性的詳細資訊，請參閱[保護散發者](../../relational-databases/replication/security/secure-the-distributor.md)。  
  
## <a name="see-also"></a>另請參閱  
 [[設定散發]](../../relational-databases/replication/configure-distribution.md)   
 [設定發行和散發](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [檢視及修改散發者和發行者屬性](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  
