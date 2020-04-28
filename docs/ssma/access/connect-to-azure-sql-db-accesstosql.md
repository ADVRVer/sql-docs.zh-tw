---
title: 連接到 Azure SQL DB （AccessToSQL） |Microsoft Docs
ms.prod: sql
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connect to SQL Azure dialog box
ms.assetid: bf44b236-d9be-41ae-a5fd-bd73038e505f
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 0b26ddaef1373544e0df2fd9186cdf56fdafd801
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "68040636"
---
# <a name="connect-to-azure-sql-db-accesstosql"></a>連接到 Azure SQL DB （AccessToSQL）
使用 [連接到 SQL Azure] 對話方塊來連接到您想要遷移的 SQL Azure 資料庫。  
  
若要存取此對話方塊，請在 [檔案]**功能表上，選取 [連線****到 SQL Azure]**。 如果您先前已連線，此命令會**重新連接到 SQL Azure。**  
  
## <a name="options"></a>選項  
**伺服器名稱**  
  
選取或輸入用來連接到 SQL Azure 的伺服器名稱。  
  
**Database**  
  
選取 []，輸入或**流覽**資料庫名稱。  
  
> [!IMPORTANT]  
> SSMA for Access 不支援連接到 SQL Azure 中的 master 資料庫。  
  
**使用者名稱**  
  
輸入 SSMA 將用來連接到 SQL Azure 資料庫的使用者名稱  
  
**密碼**  
  
請輸入使用者名稱的密碼。  
  
**Encrypt**  
  
SSMA 建議 SQL Azure 的加密連接。  
  
## <a name="create-azure-database"></a>建立 Azure 資料庫  
若要建立新的 azure 資料庫，請遵循下列步驟  
  
1.  按一下 [連接到 SQL Azure] 對話方塊中出現的 [流覽] 按鈕  
  
2.  如果沒有資料庫，則會顯示兩個功能表項目  
  
    1.  **（找不到任何資料庫）** 已停用，且所有時間皆為灰色  
  
    2.  建立一律啟用的**新資料庫**，讓使用者能夠在 SQL azure 帳戶上建立新的 azure 資料庫。 按一下此功能表項目時，會出現 [建立 azure 資料庫] 對話方塊，其中包含資料庫名稱和大小。  
  
3.  在建立資料庫時，會將這兩個參數指定為輸入。  
  
    1.  **資料庫名稱：** 輸入資料庫名稱。  
  
    2.  **資料庫大小：** 選取您需要在 SQL Azure 帳戶中建立的資料庫大小。  
  
