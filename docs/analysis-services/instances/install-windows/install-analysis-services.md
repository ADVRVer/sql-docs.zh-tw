---
title: 安裝 Analysis Services |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0904dc53e17ed140310df38d1f63dc9fe3fc45cb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "63054297"
---
# <a name="install-sql-server-analysis-services"></a>安裝 SQL Server Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  SQL Server Analysis Services 是裝載表格式模型、 多維度 cube，以及您可以從報表、 試算表和儀表板存取的資料採礦模型的分析資料庫伺服器。  
  
 Analysis Services 是多重執行個體，這表示您可以在單一電腦上安裝多個複本或執行新的和舊版本的並存。 您安裝任何執行個體的其中一個執行三種模式，因為在安裝期間決定：多維度和資料採礦、 表格式或 SharePoint。 如果您想要使用多種模式，則每種模式都需要個別執行個體。  
  
 使用特定模式安裝伺服器之後，即可用來裝載符合該模式的方案。 例如，如果您想透過網路存取表格式模型資料，則需要表格式模式伺服器。  
  
## <a name="get-tools-and-designers"></a>取得工具和設計工具  
 SQL Server 安裝程式不再安裝用於方案設計或伺服器系統管理的模型設計工具或管理工具。 在此版本中，工具會有您可從下列連結取得的個別安裝︰  
  
-   [下載 SQL Server Management Studio (SSMS)](../../../ssms/download-sql-server-management-studio-ssms.md)  
  
-   [下載 SQL Server Data Tools (SSDT)](../../../ssdt/download-sql-server-data-tools-ssdt.md)  
  
 您將需要 SSMS 和 SSDT 使用 Analysis Services 執行個體和資料。 工具可以安裝於任何位置，但請務必在伺服器上設定連接埠，再嘗試連接。 如需詳細資訊，請參閱＜ [設定 Windows 防火牆以允許 Analysis Services 存取](../../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) ＞。  
  
## <a name="install-using-a-wizard"></a>使用精靈安裝  
 下列清單顯示 [SQL Server 安裝精靈] 中用來安裝 Analysis Services 的頁面：  
  
1.  從安裝程式的 [功能樹狀目錄] 中，選取 **[Analysis Services]** 。  
  
     ![顯示 Analsyis Services 的安裝功能樹狀結構](../../../analysis-services/instances/install-windows/media/ssas-setupas.gif "顯示 Analsyis Services 的安裝功能樹狀目錄")  
  
2.  在 Analysis Services 組態 頁面上，選取 模式。 表格式模式是預設值...  
  
     ![使用 Analysis Services 組態選項的 [設定] 頁面](../../../analysis-services/instances/install-windows/media/ssas-setupasconfig.png "與 Analysis Services 組態選項的 [設定] 頁面")  
  
  表格模式使用 xVelocity 記憶體中分析引擎 (VertiPaq)，這是表格式模型的預設儲存體。 您將表格式模型部署到伺服器之後，您可以選擇設定表格式方案，以使用 DirectQuery 磁碟儲存體作為記憶體繫結的儲存體的替代方案。  
 
 多維度和資料採礦模式使用 MOLAP 作為預設儲存體模型部署到 Analysis Services。 如果您想要直接對關聯式資料庫執行查詢，而不是將查詢資料儲存在 Analysis Services 多維度資料庫，則可以在部署到伺服器之後設定方案使用 ROLAP。  
  

  
 記憶體管理和 IO 設定可以進行調整，以在使用非預設儲存模式時取得更佳的效能。 如需詳細資訊，請參閱 [Server Properties in Analysis Services](../../../analysis-services/server-properties/server-properties-in-analysis-services.md) (Analysis Services 中的伺服器屬性)。  
  
## <a name="command-line-setup"></a>命令列安裝程式  
 SQL Server 安裝程式包含可指定伺服器模式的參數 (**ASSERVERMODE**)。 下列範例說明在表格式伺服器模式下安裝 Analysis Services 的命令列安裝程式。  
  
```  
  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /FEATURES=AS /ASSERVERMODE=TABULAR /INSTANCENAME=ASTabular /INDICATEPROGRESS /ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 **INSTANCENAME** 必須少於 17 個字元。  
  
 所有預留位置帳戶值都必須取代成有效的帳戶和密碼。  
  
 **ASSERVERMODE** 區分大小寫。  所有值都必須以大寫形式表示。 下表描述 **ASSERVERMODE**的有效值。  
  
|值|描述|  
|-----------|-----------------|  
|TABULAR|這是預設值。 如果您未設定**ASSERVERMODE**，伺服器會以表格式模式安裝。|
|MULTIDIMENSIONAL|此為選擇性的值。|  
|POWERPIVOT|此為選擇性的值。 實際上，如果您設定 **ROLE** 參數，即會自動將伺服器模式設定為 1，讓 **ASSERVERMODE** 成為 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 安裝的選用參數。 如需詳細資訊，請參閱 [Install Power Pivot from the Command Prompt](http://msdn.microsoft.com/7f1f2b28-c9f5-49ad-934b-02f2fa6b9328)。|  
  
  
## <a name="see-also"></a>另請參閱  
 [判斷 Analysis Services 執行個體的伺服器模式](../../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [表格式模型化](https://msdn.microsoft.com/library/hh212945(v=sql.110).aspx)  
  
  
