---
title: 移動啟用 FILESTREAM 功能的資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], moving a FILESTREAM-enabled database
ms.assetid: dd4d270d-9283-431a-aa6b-e571fced1893
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 33d2f34f9f2ea63f23c570c0b4ada95906649215
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68091530"
---
# <a name="move-a-filestream-enabled-database"></a>移動啟用 FILESTREAM 功能的資料庫
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  本主題將示範如何移動已啟用 FILESTREAM 功能的資料庫。  
  
> [!NOTE]  
>  這個主題的範例，需要使用在 [建立啟用 FILESTREAM 的資料庫](../../relational-databases/blob/create-a-filestream-enabled-database.md)中建立的 Archive 資料庫。  
  
### <a name="to-move-a-filestream-enabled-database"></a>移動已啟用 FILESTREAM 功能的資料庫  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，按一下 [新增查詢]  開啟 [查詢編輯器]。  
  
2.  將下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼複製到 [查詢編輯器]，然後按一下 [執行]  。 此指令碼會顯示 FILESTREAM 資料庫使用之實體資料庫檔案的位置。  
  
    ```sql  
    USE Archive  
    GO  
    SELECT type_desc, name, physical_name from sys.database_files  
    ```  
  
3.  將下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼複製到 [查詢編輯器]，然後按一下 [執行]  。 此程式碼會讓 `Archive` 資料庫離線。  
  
    ```sql  
    USE master  
    EXEC sp_detach_db Archive  
    GO  
    ```  
  
4.  建立 `C:\moved_location` 資料夾，然後將步驟 2 所列的檔案和資料夾移到這個資料夾中。  
  
5.  將下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼複製到 [查詢編輯器]，然後按一下 [執行]  。 此指令碼會將 `Archive` 資料庫設定為線上。  
  
    ```sql  
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
  
  
