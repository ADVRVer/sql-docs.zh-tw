---
title: 連接到 Azure SQL Database 使用 SQL Server Native Client |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5599bbb0aa1736ba5c88904ae5152a0d73856dc5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63213775"
---
# <a name="connecting-to-a-azure-sql-database-using-sql-server-native-client"></a>使用 SQL Server Native Client 連接至 Azure SQL 資料庫
  如需相關範例，示範如何連接到[!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)]使用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client，請參閱[開發：使用說明主題 (Windows Azure SQL Database)](https://msdn.microsoft.com/library/ee621787.aspx)。  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a>連接至 SQL 資料庫時的已知問題  
 以下是使用 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] Native Client 連接至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 時的已知問題：  
  
-   如果在階段中使用 `SQLBrowseConnect`，可能會拒絕與 `SQLBrowseConnect` 建立的連接。  例如，如果在第一次呼叫中傳送驅動程式名稱，在第二次呼叫中傳送伺服器和認證 (使用者和密碼)，然後建立連接，再於第三次呼叫中傳送資料庫名稱和語言，  則第三次呼叫會導致 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 發出 USE 陳述式以變更資料庫。 但是，[!INCLUDE[ssSDS](../../../includes/sssds-md.md)] 不支援 USE 陳述式，因此產生下列錯誤：  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [使用 SQL Server Native Client 建置應用程式](building-applications-with-sql-server-native-client.md)  
  
  
