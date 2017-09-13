---
title: "連線至 SQL Server 或 Azure SQL Database | Microsoft Docs"
ms.custom: 
ms.date: 08/25/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9803a8a0-a8f1-4b65-87b8-989b06850194
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 2d5048825b3c71ecaec5da0f6ae75277994d1697
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="connect-to-a-sql-server-or-azure-sql-database"></a>連線至 SQL Server 或 Azure SQL Database

若要使用伺服器或資料庫，您必須先連線至伺服器。 您可以同時連線至多部伺服器。

[SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md) 支援多種連線類型。 本文詳細說明如何連線至 SQL Server 與 Azure SQL Database (連線至 Azure SQL 邏輯伺服器)。 如需其他連線選項的詳細資訊，請參閱此頁面底部的[連結](#see-also)。
  
## <a name="connecting-to-a-server"></a>連接至伺服器  

1. 在**物件總管**，按一下 [連線] > [資料庫引擎...]。

   ![connect](../media/connect-to-server/connect-db-engine.png)

1. 填寫 [連線至伺服器] 表單，並按一下 [連線]：

   ![連線至伺服器](../media/connect-to-server/connect.png)

1. 若您連線至 Azure SQL Server，系統可能會提示您登入以建立防火牆規則。 按一下 [登入...]\(如果沒有，請跳至步驟 6)

   ![防火牆](../media/connect-to-server/firewall-rule-sign-in.png)

1. 登入成功後，表單會預先填入您的特定 IP 位址。 若您的 IP 位址常常變更，可能會讓其他位址更容易進行存取，因此，請選取最適合您環境的選項。 

   ![防火牆](../media/connect-to-server/new-firewall-rule.png)

1. 若要建立防火牆規則並連線至伺服器，請按一下 [確定]。

1. 成功連線後，伺服器會顯示在**物件總管**中：

   ![已連線](../media/connect-to-server/connected.png)

## <a name="next-steps"></a>後續步驟

[設計、建立及更新資料表](../visual-db-tools/design-tables-visual-database-tools.md)

## <a name="see-also"></a>另請參閱

[SQL Server Management Studio (SSMS)](../sql-server-management-studio-ssms.md)  
[下載 SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md)

[Analysis Services (英文)](https://docs.microsoft.com/sql/analysis-services/instances/connect-to-analysis-services)  
[Integration Services](https://docs.microsoft.com/sql/integration-services/sql-server-integration-services)  
[Reporting Services](https://docs.microsoft.com/sql/reporting-services/tools/connect-to-a-report-server-in-management-studio)  
[Azure 儲存體](../f1-help/connect-to-microsoft-azure-storage.md)  

