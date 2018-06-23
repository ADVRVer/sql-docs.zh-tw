---
title: 安裝 SQL Server BI 功能與 SharePoint （PowerPivot 和 Reporting Services） |Microsoft 文件
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3166107c-30c2-468e-bb1b-bb42b79b37c3
caps.latest.revision: 20
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 25c8c6d8c5d83ba3661d30ed85f560d0aa18a54d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36031366"
---
# <a name="install-sql-server-bi-features-with-sharepoint-powerpivot-and-reporting-services"></a>安裝具有 SharePoint 的 SQL Server BI 功能 (PowerPivot 和 Reporting Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 和[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]可以與啟用 SharePoint 中的商業智慧 (BI) 功能的 Microsoft SharePoint 伺服陣列整合。 功能包括[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]， [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]，和[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 用於[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]SharePoint 伺服陣列中的資料存取。 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 是一種資料引擎，適用於以 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel 建立並從 SharePoint 文件庫存取的活頁簿。 一旦儲存之後[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]至 SharePoint 的活頁簿，您可以使用它做為資料來源[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]報表。  
  
 SharePoint 2010 所需的一些安裝和組態步驟和 SharePoint 2013 所需要的步驟不同。 本節的部分主題同時適用於 SharePoint 的這兩個版本。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010|  
  
 ![請注意](../../../2014/reporting-services/media/rs-fyinote.png "注意")目前的版本資訊，請參閱[SQL server 2014 版本資訊](http://go.microsoft.com/fwlink/?LinkID=296445)。  
  
##  <a name="bkmk_top"></a> 本主題內容  
  
-   [SQL Server BI 案例和 SharePoint 2013](#bkmk_bi_scenarios)  
  
-   [安裝概觀](#bkmk_install_sharepoint2013_overview)  
  
## <a name="in-this-section"></a>本節內容  
 除了本主題中的資訊以外，本節內容還包含下列相關主題。  
  
 [在 SharePoint 中的 SQL Server BI 功能的部署拓撲](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)  
  
 [使用 SharePoint 2010 伺服陣列中的 SQL Server BI 功能的指引](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
 [使用 SharePoint 安裝 BI 功能的檢查清單](../../../2014/sql-server/install/checklists-for-installing-bi-features-with-sharepoint.md)  
  
 [Reporting Services SharePoint 模式安裝&#40;SharePoint 2010 和 SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)  
  
 [PowerPivot for SharePoint 2013 安裝](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
 [PowerPivot for SharePoint 2010 安裝](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
##  <a name="bkmk_bi_scenarios"></a> SQL Server BI 案例和 SharePoint 2013  
 本節摘要您可以選擇安裝和設定的不同 BI 功能層級。  
  
 SharePoint 2013 中的 Excel Services 包含資料模型功能，可在瀏覽器中啟用與 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 活頁簿的互動。 基本資料模型功能您不需要部署[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2013年增益集至伺服器陣列。 您只需要在 SharePoint 模式下安裝 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器，並且在 Excel Services **[資料模型]** 設定中註冊伺服器即可。  
  
 部署[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2013年增益集可以讓其他功能與 SharePoint 伺服器陣列中的特性。 其他功能包括[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]圖庫、 排程資料重新整理及 PowerPivot 管理儀表板。 請參閱下表以取得其他資訊。  
  
||層級|功能|安裝或設定|  
|-|-----------|--------------|--------------------------|  
|@shouldalert|僅 SharePoint|原生 Excel Services 功能|Excel Services 以及 SharePoint Server 2013 隨附的其他服務。|  
|**2**|SharePoint 以及 SharePoint 模式的 Analysis Services|在瀏覽器中的互動式 PowerPivot 活頁簿|以 SharePoint 模式安裝 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。<br /><br /> 在 Excel Services 中註冊 Analysis Services 伺服器。|  
|**3**|SharePoint 以及 SharePoint 模式的 Reporting Services|Power View|以 SharePoint 模式安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。<br /><br /> 安裝[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]增益集 **(rsSharePoint.msi)** for SharePoint。 如需詳細資訊，請參閱[安裝或解除安裝 Reporting Services 增益集的 SharePoint &#40;SharePoint 2010 和 SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)|  
|**4**|所有 PowerPivot 功能|存取活頁簿做為來自於伺服器陣列外部的資料來源。<br /><br /> 排程資料重新整理。<br /><br /> PowerPivot 圖庫。<br /><br /> 管理儀表板。<br /><br /> BISM 連結檔案內容類型。|部署 PowerPivot for SharePoint 2013 增益集 **(spPowerPivot.msi)**。 如需詳細資訊，請參閱下列內容：<br /><br /> [安裝或解除安裝 PowerPivot for SharePoint 增益集&#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)<br /><br /> 如需有關如何下載 **spPowerPivot.msi**的詳細資訊，請參閱＜ [下載 SQL Server 2014 PowerPivot for SharePoint](http://go.microsoft.com/fwlink/?LinkID=296473)＞。|  
  
 如需有關啟用[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]功能，請參閱[SQL Server BI Light-up Story for SharePoint 2013](http://blogs.msdn.com/b/analysisservices/archive/2012/07/27/introducing-the-bi-light-up-story-for-sharepoint-2013.aspx) (http://blogs.msdn.com/b/analysisservices/archive/2012/07/27/introducing-the-bi-light-up-story-for-sharepoint-2013.aspx)。  
  
##  <a name="bkmk_install_sharepoint2013_overview"></a> 安裝概觀  
 如果您想要同時使用[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]和[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]，執行 SQL Server 安裝精靈 兩次。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 和[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]上是不同選項**安裝程式角色**SQL Server 安裝精靈的頁面。  
  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 支援 SharePoint 2010 和 SharePoint 2013。但不同的架構和安裝程序會根據 SharePoint 版本使用。  
  
 以下將摘要說明在單一伺服器上部署 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] BI 功能的安裝步驟：  
  
 **[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013**  
  
 如**SharePoint 2013**、[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]安裝可在未安裝 SharePoint 產品的伺服器上執行。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] For SharePoint 2013 中使用的架構是執行**外**SharePoint 伺服器陣列，可以安裝在也包含 SharePoint 安裝的伺服器上，或它可以是安裝不包含伺服器SharePoint 安裝。  
  
1.  安裝 SharePoint Server 2013 並啟用 Excel Services。  
  
2.  以 SharePoint 模式安裝 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]，並且在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中，將伺服器管理員權限授與 SharePoint 伺服器陣列及服務帳戶。  
  
     這兩個版本的 SharePoint，[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]藉由選取的安裝程式角色的安裝程序開始**SQL Server PowerPivot for SharePoint**在 SQL Server 安裝精靈或使用 SQL Server 命令提示字元安裝。  
  
     ![安裝程式角色](../../../2014/sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "安裝程式角色")  
  
3.  For SharePoint 2013，您可以擴充[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]功能和體驗。 下載並執行**spPowerPivot.msi**加入伺服器端資料重新整理處理、 共同作業及管理支援[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]活頁簿。 如需詳細資訊，請參閱＜ [Microsoft SQL Server 2014 PowerPivot for Microsoft® SharePoint](http://go.microsoft.com/fwlink/?LinkID=324854)＞。  
  
     執行[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2013年安裝套件**spPowerPivot.msi**以確保資料的正確版本的 SharePoint 伺服陣列中每部伺服器上安裝提供者。  
  
4.  若要設定[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]for SharePoint 2013 使用**PowerPivot for SharePoint 2013 組態**工具。  
  
     SQL Server 安裝精靈會安裝兩個[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]組態工具。 其中一個組態工具支援 SharePoint 2013，另一個工具則支援 SharePoint 2010。  
  
     ![兩個 PowerPivot 組態工具](../../../2014/analysis-services/media/as-powerpivot-configtools-bothicons.gif "兩個 PowerPivot 組態工具")  
  
5.  在 SharePoint Server 2013 中設定 Excel Services，以使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體。 如需詳細資訊，請參閱 < 設定基本 Analysis Services SharePoint 整合 > 一節中[PowerPivot for SharePoint 2013 安裝](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)和[管理 Excel Services 資料模型設定 (SharePoint Server2013)](http://technet.microsoft.com/library/jj219780.aspx) (http://technet.microsoft.com/library/jj219780.aspx)。  
  
6.  如需詳細資訊，請參閱[PowerPivot for SharePoint 2013 安裝](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)。  
  
 **[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010**  
  
 若為 SharePoint 2010，則需要在已經安裝或將會安裝 SharePoint 2010 的伺服器上執行 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint 安裝。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]執行適用於 SharePoint 2010 架構**內**伺服陣列，所以 SharePoint 必須在伺服器上的[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]安裝適用於 SharePoint 的。  
  
1.  以 SharePoint 模式安裝 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]，並且在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中，將伺服器管理員權限授與 SharePoint 伺服器陣列及服務帳戶。  
  
     SharePoint 2010 部署不支援 spPowerPivot.msi，使用 SharePoint 2010 時 **不** 需要此 .msi。  
  
     這兩個版本的 SharePoint，[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]藉由選取的安裝程式角色的安裝程序開始**SQL Server PowerPivot for SharePoint**在 SQL Server 安裝精靈或使用 SQL Server 命令提示字元安裝。  
  
2.  SQL Server 安裝精靈會安裝兩個[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]組態工具。 其中一個組態工具支援 SharePoint 2013，另一個工具則支援 SharePoint 2010。  
  
     若要設定[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]適用於 SharePoint 2010 使用**PowerPivot 組態工具**。  
  
3.  如需詳細資訊，請參閱＜ [PowerPivot for SharePoint 2010 Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)＞。  
  
 **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]**  適用於 SharePoint 2010 和 2013  
  
1.  安裝[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]在 SharePoint 模式是不變，與舊版相同。  
  
     [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]適用於 SharePoint 2010 和 SharePoint 2013 的安裝步驟是非常類似。 有關 SharePoint 版本的重要注意事項如下：  
  
    -   查看下列項目的支援組合：  
  
        -   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的版本。  
  
        -   適用於 SharePoint 產品的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集。  
  
        -   SharePoint 產品的版本。  
  
         [支援的 SharePoint 與 Reporting Services 伺服器與增益集組合&#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
    -   SharePoint 2010 上的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 需要 SharePoint 2010 Service Pack 2 (SP2)。  
  
    1.  以 SharePoint 模式安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。 [Reporting Services SharePoint 模式安裝&#40;SharePoint 2010 和 SharePoint 2013&#41; ](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)和[Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)。  
  
    2.  安裝 SharePoint 產品的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集 (rsSharePoint.msi)。 請參閱[安裝或解除安裝 Reporting Services 增益集，sharepoint &#40;SharePoint 2010 和 SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)。 目前版本的[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的 SharePoint 增益集，請參閱[如何尋找 Reporting Services 增益集適用於 SharePoint 產品](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)。  
  
    3.  設定[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 服務以及至少一個[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]服務應用程式。 如需詳細資訊，請參閱 < > 一節 < 建立 Reporting Services 服務應用程式 」 在[安裝 Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)。  
  
##  <a name="bkm_database_attach"></a> 概觀資料庫附加升級和 SharePoint 2013  
 SharePoint 2013 不支援就地升級。 不過， **支援資料庫附加升級**。  
  
 如果您擁有與 SharePoint 2010 整合的現有 PowerPivot 安裝，就無法就地升級 SharePoint 伺服器。  不過，您可以在 SharePoint 資料庫附加升級中完成下列步驟：  
  
1.  安裝新的 SharePoint Server 2013 伺服器陣列。  
  
2.  完成 SharePoint 資料庫附加升級，並且將 PowerPivot 相關的內容資料庫移轉至 SharePoint 2013 伺服器陣列。  
  
3.  以 SharePoint 模式安裝的 SQL Server Analysis Services 執行個體，並將 SharePoint 伺服器陣列與服務帳戶、 伺服器管理員權限授與[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。  
  
4.  在 SharePoint 伺服器陣列中的每部伺服器上安裝 PowerPivot for SharePoint 2013 安裝套件 **spPowerPivot.msi** 。  
  
5.  在 SharePoint 2013 管理中心內，將 Excel Services 設定為使用以 SharePoint 模式執行的 Analysis Services 伺服器 (在步驟 3 中建立)。  
  
     若要移轉重新整理排程，請設定 PowerPivot 服務應用程式。  
  
> [!NOTE]  
>  如需有關 PowerPivot 和 SharePoint 資料庫附加升級的詳細資訊，請參閱下列主題：  
  
-   [將 PowerPivot 移轉至 SharePoint 2013](../../analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013.md)  
  
-   [升級到 SharePoint 2013 的程序概觀](http://go.microsoft.com/fwlink/p/?LinkId=256688)。  
  
-   [升級到 SharePoint 2013 之前的清除準備工作](http://go.microsoft.com/fwlink/p/?LinkId=256689)。  
  
-   [將資料庫從 SharePoint 2010 升級到 SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256690)。  
  
## <a name="see-also"></a>另請參閱  
 [尋找適用於 SharePoint 產品之 Reporting Services 增益集的位置](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [支援的 SharePoint 與 Reporting Services 伺服器與增益集組合&#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)   
 [安裝或解除安裝 Reporting Services 增益集，sharepoint &#40;SharePoint 2010 和 SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  