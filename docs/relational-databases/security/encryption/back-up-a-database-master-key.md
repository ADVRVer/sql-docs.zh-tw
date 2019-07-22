---
title: 備份資料庫主要金鑰 | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], exporting
ms.assetid: 7ad9a0a0-6e4f-4f7b-8801-8c1b9d49c4d8
author: aliceku
ms.author: aliceku
ms.openlocfilehash: 0a45b7977d19603387e51b9ed824d9e8a4d759b7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997679"
---
# <a name="back-up-a-database-master-key"></a>備份資料庫主要金鑰
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ，備份 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中的資料庫主要金鑰。 資料庫主要金鑰可用來加密資料庫內部的其他金鑰和憑證。 如果遭到刪除或損毀， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可能就無法解密那些金鑰，而使用這些金鑰加密的資料實際上等於遺失了。 因此，您應該備份資料庫主要金鑰，並將該備份存放在安全且位於異地的位置。  
  
## <a name="before-you-begin"></a>開始之前  
  
### <a name="limitations-and-restrictions"></a>限制事項  
  
- 主要金鑰必須開啟，因此，將它備份之前必須先將它解密。 如果是利用服務主要金鑰來加密主要金鑰，則不必明確開啟主要金鑰。 不過，如果只利用密碼加密主要金鑰，則必須明確開啟主要金鑰。  
  
- 我們建議您在建立主要金鑰後立即將它備份，然後將該備份儲存在安全的離站位置。  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>權限
需要資料庫的 CONTROL 權限。  
  
## <a name="using-sql-server-management-studio-with-transact-sql"></a>搭配 Transact-SQL 使用 SQL Server Management Studio  
  
### <a name="to-back-up-the-database-master-key"></a>若要備份資料庫主要金鑰  
  
1. 在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中，連接到包含要備份之資料庫主要金鑰的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。  
  
2. 選擇要在備份媒體上用於加密資料庫主要金鑰的密碼。 這個密碼必須遵守複雜性檢查。  
  
3. 取得抽取式備份媒體以便儲存備份金鑰的副本。  
  
4. 識別要在其中建立金鑰備份的 NTFS 目錄。 這是建立下個步驟指定之檔案所在的位置。 這個目錄應該使用具有高度限制性的存取控制清單 (ACL) 加以保護。  
  
5. 在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。  
  
6. 在標準列上，按一下 **[新增查詢]** 。  
  
7. 複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。  
  
    ```sql
    -- Creates a backup of the "AdventureWorks2012" master key. Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;   
    GO  
    OPEN MASTER KEY DECRYPTION BY PASSWORD = 'sfj5300osdVdgwdfkli7';   
  
    BACKUP MASTER KEY TO FILE = 'c:\temp\exportedmasterkey'   
        ENCRYPTION BY PASSWORD = 'sd092735kjn$&adsg';   
    GO  
    ```  
  
    > [!NOTE]  
    > 金鑰的檔案路徑和金鑰的密碼 (如果有) 不同於上方指示。 請確定兩者都是您伺服器和金鑰設定專用的。  
  
8. 將檔案複製到備份媒體，並確認複製後的副本。  
  
9. 將備份存放在安全且位於異地的位置。  
  
 如需詳細資訊，請參閱 [OPEN MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/open-master-key-transact-sql.md) (開啟主要金鑰 (Transact-SQL)) 和 [BACKUP MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/backup-master-key-transact-sql.md) (備份主要金鑰 (Transact-SQL))。  
