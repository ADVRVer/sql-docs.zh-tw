---
title: 將 UCP 從一個 SQL Server 執行個體移到另一個 (SQL Server 公用程式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b402fd9e-0bea-4c38-a371-6ed7fea12e96
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b4518884b3fe17ea3a638ed21210775af7c4921c
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2018
ms.locfileid: "52793960"
---
# <a name="move-a-ucp-from-one-instance-of-sql-server-to-another-sql-server-utility"></a>將 UCP 從一個 SQL Server 執行個體移到另一個 (SQL Server 公用程式)
  此主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]執行個體之間移動公用程式控制點 (UCP)。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="move-a-ucp-from-one-instance-of-sql-server-to-another"></a>將 UCP 從一個 SQL Server 執行個體移到另一個  
  
1.  在將會是新的 UCP 主機執行個體的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上建立新的 UCP。 如需詳細資訊，請參閱[建立 SQL Server 公用程式控制點 &#40;SQL Server 公用程式&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md)。  
  
2.  如果您已經在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式內針對任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體設定非預設原則設定，請記下原則臨界值，好讓您可以在新的 UCP 上重新建立。 當執行個體加入至新的 UCP 時，將會套用預設的原則。 如果預設原則有效， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式清單檢視會在 **[原則類型]** 資料行中顯示 **[全域]** 。  
  
3.  從舊的 UCP 中移除所有受管理的執行個體。 如需詳細資訊，請參閱 [從 SQL Server 公用程式中移除 SQL Server 執行個體](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)。  
  
4.  從舊的 UCP 備份公用程式的管理資料倉儲 (UMDW)。 檔案名稱為 Sysutility_mdw_\<GUID>_DATA，資料庫預設位置為 \<系統磁碟機>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\，其中 \<系統磁碟機> 通常是 C:\ 磁碟機。 如需詳細資訊，請參閱 [使用備份與還原複製資料庫](../databases/copy-databases-with-backup-and-restore.md)。  
  
5.  將 UMDW 的備份還原到新的 UCP。 如需詳細資訊，請參閱 [使用備份與還原複製資料庫](../databases/copy-databases-with-backup-and-restore.md)。  
  
6.  將執行個體註冊到新的 UCP，使其受 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式所管理。 如需詳細資訊，請參閱 [註冊 SQL Server 的執行個體 &#40;SQL Server 公用程式&#41;](enroll-an-instance-of-sql-server-sql-server-utility.md)執行個體之間移動公用程式控制點 (UCP)。  
  
7.  必要時針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]受管理的執行個體實作自訂原則定義。  
  
8.  大約等候 1 小時，讓資料收集和彙總作業完成。  
  
9. 若要重新整理資料，請以滑鼠右鍵按一下 [公用程式總管] 中的 [受管理的執行個體] 節點，然後選取 [重新整理]。 清單檢視資料會顯示在 **[公用程式總管]** 內容窗格中。 如需詳細資訊，請參閱[檢視資源健全狀況原則結果 &#40;SQL Server 公用程式&#41;](view-resource-health-policy-results-sql-server-utility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 公用程式的功能與工作](sql-server-utility-features-and-tasks.md)   
 [註冊 SQL Server 的執行個體 &#40;SQL Server 公用程式&#41;](enroll-an-instance-of-sql-server-sql-server-utility.md)  
  
  
