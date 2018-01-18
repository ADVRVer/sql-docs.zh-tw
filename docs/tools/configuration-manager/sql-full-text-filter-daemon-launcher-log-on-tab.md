---
title: "SQL 全文檢索篩選背景程式啟動器 （登入 索引標籤） |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13e260f9-a75f-430b-88a3-959ddcead8fe
caps.latest.revision: "9"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3d1c6b9e4c73f1df1aafc3940a44b51149a7121b
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="sql-full-text-filter-daemon-launcher-log-on-tab"></a>SQL 全文檢索篩選背景程式啟動器 (登入索引標籤)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]從開始[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]，就會使用 SQL 全文檢索篩選背景程式啟動器 （FDHOST 啟動器） 服務[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]全文檢索搜尋。 如果您使用全文檢索搜尋，這個服務就必須執行。 如需有關篩選背景程式主機處理序的詳細資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜全文檢索搜尋架構＞。  
  
 您可以使用 **[SQL 全文檢索篩選背景程式啟動器屬性]** 對話方塊的 **[登入]** 索引標籤來指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文檢索服務所使用的帳戶、變更帳戶的密碼，以及啟動和停止服務。 帳戶密碼的變更會在重新啟動服務之後生效。  
  
> [!NOTE]  
>  在叢集執行個體上變更服務所使用的帳戶名稱時，新帳戶必須是服務安裝期間所指定之網域群組的成員，或者您必須擁有在該群組中加入成員的權限。 如果您沒有修改群組成員資格的權限，請與網域管理員連絡。  
>   
>  如需有關選取帳戶以執行服務的詳細資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜設定 Windows 服務帳戶＞。  
  
## <a name="options"></a>選項。  
 **內建帳戶**  
 **本機系統**  
 指定本機系統帳戶。 這個帳戶不需要密碼。 但是，根據授與帳戶的權限，本機系統帳戶可能會禁止服務與其他伺服器互動。  
  
 **本機服務**  
 指定本機服務帳戶。 這個帳戶不需要密碼。 但是，根據授與帳戶的權限，本機服務帳戶可能會禁止服務與其他伺服器互動。  
  
 **網路服務**  
 我們建議您不要針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務，使用網路服務帳戶。 本機使用者或網域使用者帳戶更適合這些服務。  
  
 **這個帳戶**  
 指定使用 Windows 驗證的本機或網域使用者帳戶。 建議您使用具有最少服務權限的網域使用者帳戶。  
  
 **帳戶名稱**  
 指定本機或網域使用者帳戶名稱。  
  
 **密碼**  
 輸入帳戶的密碼。  
  
 **確認密碼**  
 再次輸入帳戶的密碼。  
  
 **啟動**  
 啟動服務。  
  
 **停止**  
 停止服務。  
  
 **暫停**  
 暫停服務。 不適用於這項服務。  
  
 **繼續**  
 繼續已暫停的服務。  
  
  
