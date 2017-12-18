---
title: "設定資料庫引擎存取的檔案系統權限 | Microsoft Docs"
ms.custom: 
ms.date: 06/06/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file system permissions
- service account [SQL Server], file system permissions
- permissions [SQL Server], file system
ms.assetid: 78bba43c-4edb-4216-84ac-d6246ae5546d
caps.latest.revision: "9"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: c3c16fe40753700a0f8e6d89c403b7a96324d366
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2017
---
# <a name="configure-file-system-permissions-for-database-engine-access"></a>設定 Database Engine 對檔案系統的存取權限
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] 本主題描述如何授與 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]，對資料庫檔案儲存位置的檔案系統存取權。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服務必須具有 Windows 檔案系統權限，才能存取資料庫檔案儲存所在的檔案資料夾。 其對於預設位置的權限，在安裝期間即已設定妥。 如果您將資料庫檔案放在不同的位置，可能就必須依照下列步驟授與 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 對該位置的完整控制權限。  
  
 從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 開始，權限會指派給其每一項服務的個別服務 SID。 這樣的系統有助於服務隔離並提供深層防禦。 個別服務 SID 是衍生自服務名稱，而且每一項服務各有獨特的值。 [設定 Windows 服務帳戶與權限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) 主題描述了個別服務 SID，並且在 **Windows 權限和權利**一節中提供各種名稱。 檔案位置的存取權限必須指派給此個別服務 SID。  
  
## <a name="to-grant-file-system-permission-to-the-per-service-sid"></a>若要將檔案系統權限授與個別服務 SID  
  
1.  使用 [Windows 檔案總管]，導覽到資料庫檔案儲存所在的檔案系統位置。 以滑鼠右鍵按一下檔案系統資料夾，然後按一下 [內容]。  
  
2.  在 [安全性] 索引標籤上，按一下 [編輯]，然後按一下 [新增]。  
  
3.  在 [選取使用者、電腦、服務帳戶或群組] 對話方塊中，按一下 [位置]，並從位置清單頂端選取您的電腦名稱，然後按一下 [確定]。  
  
4.  在 [輸入要選取的物件名稱] 方塊中，輸入線上叢書主題[**設定 Windows 服務帳戶與權限**](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)所列個別服務 SID 的名稱  ([!INCLUDE[ssDE](../../includes/ssde-md.md)] 的個別服務 SID 名稱是使用 **NT SERVICE\MSSQLSERVER** 代表預設執行個體，使用 **NT SERVICE\MSSQL$InstanceName** 代表具名執行個體)。  
  
5.  按一下 [檢查名稱]，驗證輸入項  (如果驗證失敗，可能是找不到名稱的緣故)。 當您按一下[確定] 時，[找到多個相符名稱] 對話方塊隨即出現。 這時，請選取個別服務 SID 名稱 (即 [MSSQLSERVER] 或 [NT SERVICE\MSSQL$InstanceName])，然後按一下 [確定]。  再按一次 [確定] 返回 [權限] 對話方塊。   
6.  在 [群組或使用者名稱] 方塊中，選取個別服務 SID 名稱，然後在 [\<名稱> 權限] 方塊中為 [完全控制] 選取 [允許] 核取方塊。  
  
7. 按一下 [套用]，再按兩次 [確定] 退出。  
  
## <a name="see-also"></a>另請參閱  
 [管理 Database Engine Services](../../database-engine/configure-windows/manage-the-database-engine-services.md)   
 [移動系統資料庫](../../relational-databases/databases/move-system-databases.md)   
 [移動使用者資料庫](../../relational-databases/databases/move-user-databases.md)  
  
  
