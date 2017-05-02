---
title: "移動啟用 FILESTREAM 功能的資料庫 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-blob
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FILESTREAM [SQL Server], moving a FILESTREAM-enabled database
ms.assetid: dd4d270d-9283-431a-aa6b-e571fced1893
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7af3800a6e604289944a340cee7f469654c495e2
ms.lasthandoff: 04/11/2017

---
# <a name="move-a-filestream-enabled-database"></a>移動啟用 FILESTREAM 功能的資料庫
  本主題將示範如何移動已啟用 FILESTREAM 功能的資料庫。  
  
> [!NOTE]  
>  這個主題的範例，需要使用在 [建立啟用 FILESTREAM 的資料庫](../../relational-databases/blob/create-a-filestream-enabled-database.md)中建立的 Archive 資料庫。  
  
### <a name="to-move-a-filestream-enabled-database"></a>移動已啟用 FILESTREAM 功能的資料庫  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，按一下 [新增查詢]**** 開啟 [查詢編輯器]。  
  
2.  將下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼複製到 [查詢編輯器]，然後按一下 [執行]****。 此指令碼會顯示 FILESTREAM 資料庫使用之實體資料庫檔案的位置。  
  
    ```tsql  
    USE Archive  
    GO  
    SELECT type_desc, name, physical_name from sys.database_files  
    ```  
  
3.  將下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼複製到 [查詢編輯器]，然後按一下 [執行]****。 此程式碼會讓 `Archive` 資料庫離線。  
  
    ```tsql  
    USE master  
    EXEC sp_detach_db Archive  
    GO  
    ```  
  
4.  建立 `C:\moved_location` 資料夾，然後將步驟 2 所列的檔案和資料夾移到這個資料夾中。  
  
5.  將下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼複製到 [查詢編輯器]，然後按一下 [執行]****。 此指令碼會將 `Archive` 資料庫設定為線上。  
  
    ```tsql  
    CREATE DATABASE Archive ON  
    PRIMARY ( NAME = Arch1,  
        FILENAME = 'c:\moved_location\archdat1.mdf'),  
    FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
        FILENAME = 'c:\moved_location\filestream1')  
    LOG ON  ( NAME = Archlog1,  
        FILENAME = 'c:\moved_location\archlog1.ldf')  
    FOR ATTACH  
    GO  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)  
  
  
