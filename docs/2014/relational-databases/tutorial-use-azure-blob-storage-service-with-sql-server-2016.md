---
title: 在 Windows Azure 儲存體服務教學課程： SQL Server 資料檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e69be67d-da1c-41ae-8c9a-6b12c8c2fb61
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f805d7a9b0997d9f5a7cecbf61b5120bdf09f3cd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323858"
---
# <a name="tutorial-sql-server-data-files-in-windows-azure-storage-service"></a>教學課程：Windows Azure 儲存體服務中的 SQL Server 資料檔案
  歡迎使用 Windows Azure 儲存體服務中的 SQL Server 資料檔案教學課程。 本教學課程可協助您了解如何直接將 SQL Server 資料檔案儲存在 Windows Azure Blob 儲存體服務中。  
  
 Windows Azure Blob 儲存體服務的 SQL Server 整合支援是 SQL Server 2014 增強功能。 如需功能的概觀和使用這項功能的優點，請參閱[在 Windows Azure 中的 SQL Server 資料檔案](databases/sql-server-data-files-in-microsoft-azure.md)。  
  
## <a name="what-you-will-learn"></a>學習內容  
 本教學課程會在多項課程中為您示範如何將 SQL Server 資料檔案儲存在 Windows Azure 儲存體服務中。 每一課都會將重點放在特定工作上。 首先，您將學習如何在 Windows Azure 中建立儲存體帳戶和容器。 然後，您將學習如何建立 SQL Server 認證，以便整合 SQL Server 與 Windows Azure 儲存體。 然後，您將直接在 Windows Azure 儲存體中建立資料庫。 此外，本教學課程會示範加密、移轉以及備份與還原案例。  
  
 本教學課程分成九個課程：  
  
 **[第 1 課： 建立 Windows Azure 儲存體帳戶和容器](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**  
 在這一課，您會建立 Windows Azure 儲存體帳戶和容器。  
  
 **[第 2 課。在容器上建立原則，並產生共用存取簽章&#40;SAS&#41;索引鍵](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**  
 在這一課，您會在 Blob 容器上建立原則以及產生共用存取簽章。  
  
 **[第 3 課： 建立 SQL Server 認證](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**  
 在這一課，您會建立認證以儲存用來存取 Windows Azure 儲存體帳戶的安全性資訊。  
  
 **[第 4 課： 建立 Windows Azure 儲存體中的資料庫](../relational-databases/lesson-3-database-backup-to-url.md)**  
 在這一課，您會使用 CREATE Database FILENAME 選項，在 Windows Azure 儲存體中建立資料庫。  
  
 **[第 5 課。&#40;選擇性&#41;加密您的資料庫使用 TDE](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**  
 在這一課，您會使用透明資料加密 (TDE) 和伺服器憑證來加密資料庫。  
  
 **[第 6 課： 將資料庫移轉來源機器內部部署至 Windows Azure 中的目的地電腦](lesson-5-backup-database-using-file-snapshot-backup.md)**  
 在這一課，您會使用 CREATE DATABASE FOR ATTACH 選項，將資料庫從內部部署移轉至 Windows Azure 中的虛擬機器。  
  
 **[第 7 課： 將資料檔案移至 Windows Azure 儲存體](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**  
 在這一課，您會使用 ALTER DATABASE 陳述式，將資料檔案移至 Windows Azure 儲存體。  
  
 **[第 8 課：將資料庫還原至 Windows Azure 儲存體](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**  
 在這一課，您會使用 RESTORE Database MOVE 選項，將資料庫還原至 Windows Azure 儲存體。  
  
 **[第 9 課。從 Windows Azure 儲存體還原資料庫](lesson-8-restore-as-new-database-from-log-backup.md)**  
 在這一課，您會使用 RESTORE Database MOVE 選項，從 Windows Azure 儲存體還原資料庫。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Azure 中的 SQL Server 資料檔案](databases/sql-server-data-files-in-microsoft-azure.md)  
  
  
