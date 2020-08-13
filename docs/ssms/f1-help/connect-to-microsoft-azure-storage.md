---
title: 連接到 Microsoft Azure 儲存體
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.windowsazurestorage.connect.f1
- SQL13.SWB.WINDOWSAZURESTORAGE.CONNECT.F1
ms.assetid: ''
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 07/12/2017
ms.openlocfilehash: f88bafe27da30ceec6154bf64cd9ced0046f7e87
ms.sourcegitcommit: d855def79af642233cbc3c5909bc7dfe04c4aa23
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87123079"
---
# <a name="connect-to-microsoft-azure-storage"></a>連接到 Microsoft Azure 儲存體

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
使用 [Azure 儲存體連線]  對話方塊，以指定儲存體帳戶並驗證 Azure 的連線。  
  
## <a name="options"></a>選項。  
請指定有關 Azure 帳戶的下列資訊，然後選取 [下一步] 繼續進行。  
  
1.  **儲存體帳戶** - 指定儲存體帳戶名稱。

   >[!NOTE]
   > 您只能連線到[一般目的儲存體帳戶](https://docs.microsoft.com/azure/storage/common/storage-introduction#azure-storage-services)。 連線到其他類型的儲存體帳戶可能會造成類似下面的錯誤：
   >
   >  其中一個 HTTP 標頭之值的格式不正確。 (Microsoft.SqlServer.StorageClient)。
   >
   >  遠端伺服器傳回錯誤：(400) 錯誤的要求。 (系統)

2.  **帳戶金鑰** - 針對指定的儲存體帳戶指定帳戶金鑰。  
  
3.  **使用安全端點 (HTTPS)** - 這個選項會利用網路 Web 伺服器的加密通訊和安全識別。  
  
4.  **儲存帳戶金鑰** - 這個選項會將您的密碼儲存在加密的檔案中。  
  
