---
title: 連接到 Azure SQL DB (AccessToSQL) |Microsoft 文件
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Connect to SQL Azure dialog box
ms.assetid: bf44b236-d9be-41ae-a5fd-bd73038e505f
caps.latest.revision: 17
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 511c652a221ffb3fe4392dd8f4c365de129efe13
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2018
---
# <a name="connect-to-azure-sql-db-accesstosql"></a>連接到 Azure SQL DB (AccessToSQL)
使用 [連線到 SQL Azure] 對話方塊中，連接到您想要移轉 SQL Azure 資料庫。  
  
若要存取此對話方塊，請在**檔案**功能表上，選取**連接到 SQL Azure**。 如果您之前已連線，則命令是**重新連接到 SQL Azure。**  
  
## <a name="options"></a>選項  
**伺服器名稱**  
  
選取或輸入伺服器名稱來連接到 SQL Azure。  
  
**資料庫**  
  
選取、 輸入或**瀏覽**資料庫名稱。  
  
> [!IMPORTANT]  
> SSMA for Access 不支援 SQL Azure 中的 master 資料庫的連接。  
  
**使用者名稱**  
  
輸入 SSMA 將用來連接到 SQL Azure 資料庫的使用者名稱  
  
**密碼**  
  
請輸入使用者名稱的密碼。  
  
**Encrypt**  
  
SSMA 會建議加密的連接到 SQL Azure。  
  
## <a name="create-azure-database"></a>建立 Azure 的資料庫  
若要建立新的 azure 資料庫，請遵循下列步驟  
  
1.  按一下 [瀏覽] 按鈕會出現在 [連接到 SQL Azure] 對話方塊  
  
2.  如果有任何資料庫，會出現兩個功能表項目  
  
    1.  **（找不到資料庫）**是停用，隨時都呈現灰色  
  
    2.  **建立新的資料庫**其永遠啟用，讓使用者能夠在 SQL Azure 帳戶上建立新的 azure 資料庫。 按一下這個功能表項目後, 建立 azure 資料庫對話方塊就會出現以資料庫名稱和大小。  
  
3.  在建立資料庫時，這兩個參數是指定為輸入。  
  
    1.  **資料庫名稱：**輸入資料庫名稱。  
  
    2.  **資料庫大小：**選取您要在 SQL Azure 帳戶中建立的資料庫大小。  
  
