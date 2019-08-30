---
title: 第 4 課：從完整資料庫備份執行還原 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 580f76e6-9802-4abc-9043-db6de592c733
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: de9a356589ac6bceb532ed4cecf509f957e3c337
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153405"
---
# <a name="lesson-4-perform-a-restore-from-a-full-database-backup"></a>第 4 課：從完整資料庫備份執行還原
  這一課將示範如何使用 tsql 陳述式，從上一課建立的完整資料庫備份執行還原。  
  
## <a name="perform-a-restore-of-a-database-backup"></a>執行資料庫備份的還原  
 若要還原完整資料庫備份，請使用下列步驟：  
  
1.  連接到 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。  
  
2.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]的執行個體。  
  
3.  在 [標準] 功能表列上，按一下 **[新增查詢]** 。  
  
4.  將下列範例複製並貼入查詢視窗中，並視需要修改。  
  
    ```  
    RESTORE DATABASE AdventureWorks2012   
    FROM URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    WITH CREDENTIAL = 'mycredential';  
    , STATS = 5 - use this to see monitor the progress  
    GO  
  
    ```  
  
5.  確認 T-sql 語句, 然後按一下 [**執行**]  
  
### <a name="return-to-tutorials-portal"></a>返回教學課程入口網站  
 [教學課程：SQL Server 備份和還原至 Azure Blob 儲存體服務](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)。  
  
  
