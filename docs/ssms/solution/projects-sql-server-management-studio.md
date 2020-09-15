---
description: 專案 (SQL Server Management Studio)
title: 專案 (SQL Server Management Studio)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c13af859-ca66-4e43-b76a-0650ac6566c0
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 321257f45a593afdaf8c69228b2018347074d7ce
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88417874"
---
# <a name="projects-sql-server-management-studio"></a>專案 (SQL Server Management Studio)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 專案是邏輯關聯之指令碼和檔案的集合，它們可以儲存在一起，以便進行資料庫的管理和開發。  
  
## <a name="script-project-overview"></a>指令碼專案概觀  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指令碼專案會顯示在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]的方案總管元件中。 指令碼專案可以包含零或多個專案檔。 您可以將專案加入方案中，或在方案內組合多個專案。  
  
專案可以包含下列各項：  
  
-   **連接**。 連接會保存在專案內，其中含有登入資訊、伺服器名稱、預設資料庫、慣用的通訊協定、驗證類型，以及連接屬性。 連接資訊可以選擇性地隨著指令碼而一併儲存 (請參閱下文)。  
  
-   **SQLScripts**。 使用者常用的 SQL 指令碼。 按兩下專案內的 .sql 檔，會使 SQL 編輯器開啟所選的指令碼。  
  
-   **MDX、DMX 和 XMLA 指令碼**。 使用者常用的 MDX 指令碼。 按兩下專案內的 .mdx 檔，會使編輯器開啟所選的指令碼。  
  
-   **其他**。不完全符合任何其他預設節點類型的檔案，如包含專案目標的文字檔，可以使用這個資料夾。  
  
專案也可以整合為一個原始程式碼控制系統。  
  
## <a name="connecting-to-an-instance-of-sql-server-from-a-script-project"></a>從指令碼專案連接到 SQL Server 的執行個體  
指令碼專案可包含指向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的連接。 按一下該連接，就可以連接到專案中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。 此時會開啟一個 [SQL 指令碼] 視窗，這個視窗會連接到您選取的連接所定義的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。 如果您利用採取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證的連接來開啟 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 MDX 指令碼，在啟動編輯器及載入指令碼之後，系統會利用 [連接到 SQL Server]**** 對話方塊來提示您輸入密碼。  
  
對應視窗關閉之後，連接也會關閉。  
  
若要修改有關連接的資訊，請使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的屬性視窗。  
  
## <a name="project-tasks"></a>專案工作  
  
|工作描述|主題|  
|--------------------|---------|  
|描述如何在方案中建立新的專案。|[建立專案](../../ssms/solution/create-a-project.md)|  
|描述如何將現有的專案加入方案中。|[將現有專案加入方案中](../../ssms/solution/add-an-existing-project-to-a-solution.md)|  
|描述如何變更儲存專案檔案的預設位置。|[變更專案的預設位置](../../ssms/solution/change-the-default-location-for-projects.md)|  
|描述如何檢視專案的目前屬性。|[檢視專案屬性](../../ssms/solution/view-project-properties.md)|  
|描述如何將新的項目 (例如連接或指令碼檔案) 加入專案中。|[將新項目加入專案](../../ssms/solution/add-new-items-to-a-project.md)|  
|描述如何建立查詢的連接資訊。|[在專案中建立查詢與連接的關聯性](../../ssms/solution/associate-a-query-with-a-connection-in-a-project.md)|  
|描述如何變更查詢的連接資訊。|[變更與查詢相關聯的連接](../../ssms/solution/change-the-connection-associated-with-a-query.md)|  
|描述如何變更連接屬性。|[檢視或變更專案中連接的屬性](../../ssms/solution/view-or-change-the-properties-of-a-connection-in-a-project.md)|  
  
## <a name="see-also"></a>另請參閱  
[方案總管](../../ssms/solution/solution-explorer.md)  
[解決方案 &#40;SQL Server Management Studio&#41;](../../ssms/solution/solutions-sql-server-management-studio.md)  
[方案總管原始檔控制](https://docs.microsoft.com/sql/ssms/solution/solution-explorer)  
  
