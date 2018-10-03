---
title: 發行集屬性、發行集存取清單 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.pubproperties.publicationaccesslist.f1
ms.assetid: 9587bb9e-c66c-4e70-8171-09b943ec2d50
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a9e94541f6c71da9ac40ecd34aacb11d7392b2df
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224148"
---
# <a name="publication-properties-publication-access-list"></a>發行集屬性，發行集存取清單
  **[發行集屬性]** 對話方塊的 **[發行集存取清單]** 頁面，可以讓您從發行集存取清單 (PAL) 加入與移除登入、帳戶和群組。 PAL 是保護發行者安全的主要機制。 建立發行集之後，複寫便會建立此發行集的 PAL。 PAL 的功能與 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 存取控制清單相似，其中包含被授與存取發行集的登入、帳戶和群組之清單。  
  
 當訂閱者連接到發行者或散發者並要求存取發行集時，訂閱者的登入會與 PAL 的驗證資訊比較。 如此可以為發行者提供額外的安全性，因為這會防止用戶端工具利用發行者與散發者的登入直接在發行者上進行修改。 如需詳細資訊，請參閱[保護發行者](security/secure-the-publisher.md)。  
  
## <a name="options"></a>選項。  
 **[加入]**  
 加入一個新項目到清單中。 您只能加入在發行者端和散發者端都已經定義的登入、帳戶或群組。 如果您使用網域帳戶或在兩個伺服器上都已經建立本機帳戶，則它們就已同時在兩個伺服器上定義完成。  
  
 **移除**  
 從清單中移除選取的項目。  
  
 **全部移除**  
 從清單中移除所有的項目。  
  
## <a name="see-also"></a>另請參閱  
 [Create a Publication](publish/create-a-publication.md)   
 [檢視及修改發行集屬性](publish/view-and-modify-publication-properties.md)   
 [發行資料和資料庫物件](publish/publish-data-and-database-objects.md)  
  
  
