---
title: 散發者密碼 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.configuredistributionwizard.distributorpassword.f1
ms.assetid: 52787c5e-c9ef-440e-a000-0787111b7dbb
caps.latest.revision: 24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0f3389612660a08ce7da4d7a6df207f83f0ae39e
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37356800"
---
# <a name="distributor-password"></a>散發者密碼
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  如果，在此精靈的 **[發行者]** 頁面上，您已啟用一或多個發行者使用此伺服器作為遠端散發者，則必須為發行者與使用 **distributor_admin** 登入的遠端散發者之間的連接複寫指定密碼。 針對使用此遠端散發者的每個發行者，也必須在新增發行集精靈或設定散發精靈的 **[管理密碼]** 頁面上輸入相同的密碼。 如需散發者安全性的詳細資訊，請參閱[保護散發者](../../relational-databases/replication/security/secure-the-distributor.md)。  
  
## <a name="options"></a>選項。  
 **密碼**  
 為發行者和遠端散發者之間的連接輸入增強式密碼。  
  
 **確認密碼**  
 重新輸入密碼，以確認密碼輸入正確。  
  
## <a name="see-also"></a>另請參閱  
 [[設定散發]](../../relational-databases/replication/configure-distribution.md)   
 [設定發行和散發](../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
  
