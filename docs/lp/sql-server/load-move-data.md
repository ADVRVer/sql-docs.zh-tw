---
layout: HubPage
hide_bc: true
title: SQL Server - 載入及移動資料
description: 探索可協助您使用 SQL Server 載入、移動及移轉資料庫與資料的功能。
ms.topic: hub-page
ms.prod: sql
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.date: 12/15/2018
featureFlags:
- clicktale
ms.openlocfilehash: 601bf4bdfae6b896c218d30c9b943bd1e97ba70c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63265187"
---
<div id="main" class="v2">
    <div class="container">
        <ul class="cardsY panelContent featuredContent">
            <li>
                <a href="https://www.microsoft.com/evalcenter/evaluate-sql-server-2019-ctp">
                    <div class="cardSize">
                        <div class="cardPadding">
                            <div class="card">
                                <div class="cardImageOuter">
                                    <div class="cardImage">
                                        <img src="media/index/download-sql-server.svg" alt="" />
                                    </div>
                                </div>
                                <div class="cardText">
                                    <span class="likeAnH3">試用 SQL Server 2019 (預覽)</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </a>
            </li>
            <li>
                <a href="https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm">
                    <div class="cardSize">
                        <div class="cardPadding">
                            <div class="card">
                                <div class="cardImageOuter">
                                    <div class="cardImage">
                                        <img src="media/index/get-azure-sql-vm.svg" alt="" />
                                    </div>
                                </div>
                                <div class="cardText">
                                    <span class="likeAnH3">取得含 SQL Server 的虛擬機器</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </a>
            </li>
            <li>
                <a href="/sql/ssms/download-sql-server-management-studio-ssms">
                    <div class="cardSize">
                        <div class="cardPadding">
                            <div class="card">
                                <div class="cardImageOuter">
                                    <div class="cardImage">
                                        <img src="media/index/download-ssms.svg" alt="" />
                                    </div>
                                </div>
                                <div class="cardText">
                                    <span class="likeAnH3">下載 SQL Server Management Studio</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </a>
            </li>              
        </ul>
    </div>
    <div class="container">
        <h1>SQL Server:移轉、載入及移動資料</h1>
        <ul class="pivots tabLess">
            <li class="pivotItem" style="display: list-item;" data-id="#products">
                <a href="#products" data-linktype="self-bookmark"></a>
                <ul id="products">
                    <li class="panelItem" data-index="0">
                        <a class="singlePanelNavItem selected" href="#products1" data-linktype="self-bookmark"></a>
                        <ul class="cardsD panelContent singlePanelContent" id="products1" style="margin-top: 0px; display: flex;">
                            <li class="fullSpan">
                                <div class="container intro">
                                <h2>將資料庫移轉至 SQL</h2>
                            </li>
                                                         <li>
                                <a href="/azure/dms/dms-overview/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/install-sql-and-services/adm-service.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Azure 資料庫移轉服務</h3>
                                                    <p>可讓多個資料庫來源以最短停機時間無縫移轉到 Azure 資料平台。</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/dma/dma-overview/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/install-sql-and-services/dma-assist.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Database Migration Assistant (DMA)</h3>
                                                    <p>針對您的目標環境偵測相容性問題與建議改進，並移動您的資料庫與資料。</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/ssma/sql-server-migration-assistant/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/install-sql-and-services/ssma-assist.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>SQL Server 移轉小幫手 (SSMA)</h3>
                                                    <p>自動化將資料庫從 Microsoft Access、DB2、MySQL、Oracle 與 SAP ASE 移轉至 SQL Server 的作業。</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/dea/database-experimentation-assistant-overview">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/load-move-data/database-experimentation-assistant.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>資料庫測試助理 (DEA)</h3>
                                                    <p>協助針對現有工作負載評估 SQL Server 的目標版本。</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li class="fullSpan">
                                <div class="container intro">
                                <h2>載入並移動資料</h2>
                            </li>
                            <li>
                                <a href="/sql/tools/bcp-utility/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/load-move-data/bcp.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>BCP</h3>
                                                    <p>在資料檔案與您的 SQL 資料庫之間以您指定的格式大量複製資料。</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li> 
                            <li>
                                <a href="/sql/relational-databases/import-export/import-flat-file-wizard">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/load-move-data/flat-file-import-wizard.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>匯入一般檔案精靈</h3>
                                                    <p>使用精靈以簡單的方式將資料從一般檔案 (.csv、.txt) 複製到 SQL 資料庫中。 </p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/load-move-data/import-export-wizard.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>匯入和匯出精靈</h3>
                                                    <p>使用精靈以簡單的方式將資料從各種來源複製到 SQL 資料庫中。 </p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/integration-services/sql-server-integration-services">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/load-move-data/ssis.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>SQL Server Integration Services (SSIS)</h3>
                                                    <p>可從各種來源 (如一般檔案與關聯式資料來源) 擷取及轉換資料，然後再將該資料載入到您的 SQL 資料庫。 </p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/relational-databases/replication/sql-server-replication/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/load-move-data/replication.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>複寫</h3>
                                                    <p> 一組將資料與資料庫物件從某個資料庫複製及散發到另一個資料庫，然後在兩個資料庫之間進行同步處理以維護一致性的技術。</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                        </ul>
                    </li>
                </ul>
            </li>
        </ul>
    </div>
</div>
<div class="container centered pageFooter">
        <h2>與我們保持連絡</h2>
        <ul class="links">
           <li>
                <a href="https://aka.ms/editsqldocs" data-linktype="external"> 參與 </a>
            </li>
           <li>
                <a href="https://docs.microsoft.com/sql/sql-server/sql-server-get-help" data-linktype="external"> 取得協助 </a>
            </li>
           <li>
                <a href="https://aka.ms/sqldocsfeedback" data-linktype="external"> 意見反應 </a>
            </li>
           <li>
                <a href="https://aka.ms/sqldocsurvey" data-linktype="external"> 問卷 </a>
            </li>
           <li>
                <a href="https://cloudblogs.microsoft.com/sqlserver/" data-linktype="external">部落格</a>
            </li>
            <li>
                <a href="https://twitter.com/sqldocs" data-linktype="external">Twitter</a>
            </li>
            <li>
                <a href="https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqldatabaseengine&filter=alltypes&sort=lastpostdesc" data-linktype="external">MSDN 論壇</a>
            </li>
            <li>
                <a href="https://feedback.azure.com/forums/908035-sql-server" data-linktype="external">User Voice</a>
            </li>
        </ul>
    </div>

