---
title: "備份服務主要金鑰 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service master key [SQL Server], exporting
ms.assetid: f60b917c-6408-48be-b911-f93b05796904
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 630f9c3ecdf47e6cb7a5d9f2a7970bea99d330a9
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="back-up-the-service-master-key"></a>備份服務主要金鑰
  此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ，備份 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中的服務主要金鑰。 服務主要金鑰是加密階層的根。 應該將服務主要金鑰備份並儲存在安全且位於異地的位置。 建立這個備份，應該是必須在伺服器上執行的首要管理動作之一。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [限制事項](#Restrictions)  
  
     [安全性](#Security)  
  
-   [若要備份服務主要金鑰](#Procedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Restrictions"></a> 限制事項  
  
-   主要金鑰必須開啟，因此，將它備份之前必須先將它解密。 如果是利用服務主要金鑰來加密主要金鑰，則不必明確開啟主要金鑰；如果只利用密碼加密主要金鑰，則必須明確開啟主要金鑰。  
  
-   我們建議您在建立主要金鑰後立即將它備份，然後將該備份儲存在安全的離站位置。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 需要資料庫的 CONTROL 權限。  
  
##  <a name="Procedure"></a> 使用 Transact-SQL  
  
#### <a name="to-back-up-the-service-master-key"></a>若要備份服務主要金鑰  
  
1.  在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中，連接到含有您要備份的服務主要金鑰的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。  
  
2.  選擇要在備份媒體上用於加密服務主要金鑰的密碼。 這個密碼必須遵守複雜性檢查。 如需詳細資訊，請參閱＜ [Password Policy](../../../relational-databases/security/password-policy.md)＞。  
  
3.  取得抽取式備份媒體以便儲存備份金鑰的副本。  
  
4.  識別要在其中建立金鑰備份的 NTFS 目錄。 這是建立下個步驟指定之檔案所在的位置。 這個目錄應該使用具有高度限制性的存取控制清單 (ACL) 加以保護。  
  
5.  在 **[物件總管]**中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。  
  
6.  在標準列上，按一下 **[新增查詢]**。  
  
7.  將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]**。  
  
    ```  
    -- Creates a backup of the service master key.
    USE master;
    GO
    BACKUP SERVICE MASTER KEY TO FILE = 'c:\temp_backups\keys\service_master_ key'
        ENCRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';
    GO
    ```  
  
    > [!NOTE]  
    >  金鑰的檔案路徑和金鑰的密碼 (如果有) 不同於上方指示。 請確定兩者都是您伺服器和金鑰設定專用的。  
  
8.  將檔案複製到備份媒體，並確認複製後的副本。  
  
9. 將備份存放在安全且位於異地的位置。  
  
 如需詳細資訊，請參閱 [OPEN MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/open-master-key-transact-sql.md) (開啟主要金鑰 (Transact-SQL)) 和 [BACKUP MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/backup-master-key-transact-sql.md) (備份主要金鑰 (Transact-SQL))。  
  
  

