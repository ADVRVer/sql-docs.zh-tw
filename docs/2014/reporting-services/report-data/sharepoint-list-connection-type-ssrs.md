---
title: SharePoint 清單連線類型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 2c4adf2f-e9c4-4fae-bd3c-97fe64436caf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 43864fb135faf61a2a0205199d7717d7b5c04026
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62720613"
---
# <a name="sharepoint-list-connection-type-ssrs"></a>SharePoint 清單連接類型 (SSRS)
  若要在報表中包含來自 Microsoft SharePoint 清單的資料，您必須加入或建立以 Microsoft SharePoint 清單類型之報表資料來源為基礎的資料集。 這是以 Microsoft SQL Server Reporting Services SharePoint 清單資料延伸模組為基礎的內建資料來源類型。 使用此資料來源類型可連接至 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]、 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)]、 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0 和 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007 網站，並從中擷取清單資料。  
  
 您可以使用本主題中的資訊來建置資料來源。 如需逐步指示，請參閱 <<c0> [ 加入及驗證資料連接或資料來源&#40;報表產生器及 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</c0>  
  
##  <a name="Connection"></a> 連接字串  
 SharePoint 清單的連接字串是 SharePoint 網站或子網站的 URL，例如 `http://MySharePointWeb/MySharePointSite` 或 `http://MySharePointWeb/MySharePointSite/Subsite`。  
  
 查詢設計工具會自動顯示您有足夠權限存取的 SharePoint 清單。  
  
 如需更多連接字串範例，請參閱 [報表產生器中的資料連接、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。  
  
##  <a name="Credentials"></a> 認證  
 需要有認證才能夠執行報表、於本機預覽報表並且從報表伺服器預覽報表。 發行報表之後，您可能需要變更資料來源的認證，如此當報表在報表伺服器上執行時，擷取資料的權限就會是有效的。 可搭配這個資料延伸模組使用的認證類型，取決於您使用做為資料來源之 SharePoint 清單的 SharePoint 技術設定。  
  
 下表概述當連接到本機伺服器陣列的 SharePoint 清單和遠端 SharePoint 清單時，SharePoint 清單延伸模組的認證擷取行為。  
  
 **表格 1** 適用於部署到舊版 Windows SharePoint 網站的報表。 舊版 Windows 網站僅支援 Kerberos、NTLM 和表單為主的驗證 (FBA)。 **表格 2** 適用於部署到宣告式 SharePoint 網站的報表。  
  
 **表格 1**  
  
||支援的認證|傳統模式 Windows 驗證|<sup>3</sup>宣告驗證|  
|-|---------------------------|-----------------------------------------|----------------------------------------|  
|本機伺服器陣列的 SharePoint 清單|Windows 驗證 (整合式) 或 SharePoint 使用者 Token|是|是|  
||預存、提示、無 (包含 Windows 認證<sup>1</sup>)|是|否|  
|遠端 SharePoint 清單|Windows 驗證 (整合式) 或 SharePoint 使用者 Token|是|否<sup>2</sup>|  
||預存、提示、無 (包含 Windows 認證<sup>1</sup>)|是|否<sup>2</sup>|  
  
 **表格 2**  
  
||支援的認證|傳統模式 Windows 驗證|<sup>3</sup>宣告驗證|  
|-|---------------------------|-----------------------------------------|----------------------------------------|  
|本機伺服器陣列的 SharePoint 清單|Windows 驗證 (整合式) 或 SharePoint 使用者 Token|是|是|  
||預存、提示、無 (包含 Windows 認證<sup>1</sup>)|否|否|  
|遠端 SharePoint 清單|Windows 驗證 (整合式) 或 SharePoint 使用者 Token|是|否<sup>2</sup>|  
||預存、提示、無 (包含 Windows 認證<sup>1</sup>)|否|否<sup>2</sup>|  
  
 <sup>1</sup>不支援預存和提示認證以非 Windows 認證。  
  
 <sup>2</sup>表單型驗證和宣告驗證不支援遠端 SharePoint 清單。  
  
 <sup>3</sup> Windows 驗證、 表單為主的驗證 (FBA)、 安全應用程式標記語言 (SAML) token、 其他識別提供者或上述之一個以上的組合所述的驗證提供者。  
  
 **Windows 驗證**  
 若 SharePoint 技術設為搭配「信任帳戶」模式的報表伺服器使用，則不支援此選項。 只適用於 SQL Server 2012 Reporting Services 之前的版本。  
  
 若 SharePoint 技術設為搭配「Windows 整合式」模式的報表伺服器使用，此選項會套用至目前的 Windows 使用者和目前的 SharePoint 使用者。  
  
 若 SharePoint 技術設為不搭配報表伺服器使用 (本機模式)，則不支援此選項。 如需本機模式的詳細資訊，請參閱[本機模式與本機模式與連接模式報表 &#40;SharePoint 模式的 Reporting Services&#41;](../local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md)。  
  
 **不需要認證 (請勿使用認證)：**  
 若要使用這個選項，您必須在報表伺服器上設定自動執行帳戶。 如需詳細資訊，請參閱[設定自動執行帳戶 &#40;SSRS 組態管理員&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)。  
  
 如需有關跨 Microsoft BI 堆疊之宣告驗證支援的詳細資訊，請參閱 [跨 Microsoft BI 堆疊使用宣告驗證](https://social.technet.microsoft.com/wiki/contents/articles/15274.using-claims-authentication-across-the-microsoft-bi-stack.aspx)。  
  
 如需詳細資訊，請參閱 <<c0> [ 資料連接、 資料來源和 Reporting Services 中的連接字串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)，[在 報表產生器中指定認證](../specify-credentials-in-report-builder.md)，和[所支援的資料來源Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</c0>  
  
##  <a name="Query"></a> 查詢  
 若要設計查詢，根據資料來源建立新資料集，然後開啟相關聯的查詢設計工具。 如需詳細資訊，請參閱 [建立共用資料集或內嵌資料集 &#40;報表產生器及 SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)。  
  
 SharePoint 清單圖形化查詢設計工具會顯示四個窗格：  
  
 **SharePoint 清單**  ：在此資料來源的網站上顯示所有 SharePoint 清單的清單。 選取一個清單，然後選取要位於查詢中的欄位。 在此窗格中，欄位的名稱為 SharePoint 易記名稱，也稱為顯示名稱。 將滑鼠游標停留在某個項目上，即可在工具提示中顯示下列屬性：  
  
-   **名稱** ：欄位的唯一名稱。  
  
-   **識別碼** ：欄位的唯一識別碼。  
  
-   **欄位類型** ：欄位的資料類型。  
  
-   **隱藏** ：欄位是否顯示在 SharePoint 清單檢視中。  
  
 不支援從多個清單中選取欄位。 您可為每個清單建立資料集，然後從每個資料集選取欄位。 若清單具有一般欄位，可以使用繫結到某個資料集的 Tablix 資料區中之 Lookup 函數，從未繫結到資料區的其他資料集中擷取值。 如需詳細資訊，請參閱[查閱函數 &#40;報表產生器及 SSRS&#41;](../report-design/report-builder-functions-lookup-function.md)。  
  
-   **選取的欄位**  ：顯示您已經選取的欄位。 在此窗格中，欄位的名稱為 SharePoint 使用者已經指定的易記名稱。 當您關閉查詢設計工具時，您會在 [報表資料] 窗格的資料集欄位集合中看到這些名稱。 [資料集屬性對話方塊、欄位 &#40;報表產生器&#41;](../dataset-properties-dialog-box-fields-report-builder.md) 頁面有唯一名稱和易記名稱之間的關聯性。  
  
-   **套用的篩選**  ：在資料傳回報表前，限制從 SharePoint 清單傳回的資料。 選取欄位名稱、運算子及值，用來限制在清單中擷取的資料。 這些運算子會隨著您選取之值的資料類型而有所不同。  
  
     您無法在圖形化查詢設計工具中變更排序順序或指定群組。 若要這麼做，請在報表資料集上設定排序運算式，然後針對報表中的資料區為運算式分組。 不支援查詢參數。 若要篩選報表中的資料，使用您建立的報表篩選或報表參數。 如需詳細資訊，請參閱 [篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) 和 [報表參數 &#40;報表產生器和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)。  
  
-   **查詢結果**  ：顯示查詢執行時所傳回的範例資料列。 如果 SharePoint 網站上的 SharePoint 清單值經常變更，您在查詢結果窗格中看到的值可能會與您在報表中看到的值不同。  
  
-   **選取的欄位**  ：顯示您已經選取的欄位。 在此窗格中，欄位的名稱為 SharePoint 使用者已經指定的易記名稱。 當您關閉查詢設計工具時，您會在 [報表資料] 窗格的資料集欄位集合中看到這些名稱。 [資料集屬性對話方塊、欄位 &#40;報表產生器&#41;](../dataset-properties-dialog-box-fields-report-builder.md) 頁面有唯一名稱和易記名稱之間的關聯性。  
  
-   **套用的篩選**  ：在資料傳回報表前，限制從 SharePoint 清單傳回的資料。 選取欄位名稱、運算子及值，用來限制在清單中擷取的資料。 這些運算子會隨著您選取之值的資料類型而有所不同。  
  
     您無法在圖形化查詢設計工具中變更排序順序或指定群組。 若要這麼做，請在報表資料集上設定排序運算式，然後針對報表中的資料區為運算式分組。 不支援查詢參數。 若要篩選報表中的資料，使用您建立的報表篩選或報表參數。 如需詳細資訊，請參閱 [篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) 和 [報表參數 &#40;報表產生器和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)。  
  
-   **查詢結果**  ：顯示查詢執行時所傳回的範例資料列。 如果 SharePoint 網站上的 SharePoint 清單值經常變更，您在查詢結果窗格中看到的值可能會與您在報表中看到的值不同。  
  
 如需詳細資訊，請參閱 [SharePoint 清單查詢設計工具 &#40;報表產生器&#41;](sharepoint-list-query-designer-report-builder.md)。  
  
### <a name="query-text"></a>查詢文字  
 若要檢視圖形化查詢設計工具所產生的查詢，請切換到以文字為基礎的查詢設計工具。 在此檢視中，您可以看到圖形化查詢設計工具所建立的 XML。 XML 包含清單名稱、欄位集合和篩選的元素。  
  
#### <a name="example-1-specified-fields-for-a-list"></a>範例 1： 指定清單的欄位  
 下列範例顯示格式正確的 SharePoint 查詢：  
  
```  
<RSSharePointList>  
<listName>MyList</listName>  
<viewFields>  
  <FieldRef Name="Field1"/>  
  <FieldRef Name="Field4"/>  
</viewFields>  
<Query>  
  <Where>  
    <And>  
      <Gt>  
        <FieldRef Name="Field1"/>  
        <Value Type="Integer">1</Value>  
      </Gt>  
      <IsNotNull>  
        <FieldRef Name="Field2"/>  
        <Value Type="string"/>  
      </IsNotNull>   
    </And>  
  </Where>  
</Query>  
</RSSharePointList>  
```  
  
 只要查詢維持格式正確的 XML 文字，您就可以編輯此查詢的檢視。  
  
#### <a name="example-2-all-fields-for-a-list"></a>範例 2： 清單的所有欄位  
 您也可以指定只傳回清單的名稱以及所有欄位，包括隱藏的欄位。 下列範例會從名為 Tasks 的清單擷取所有欄位：  
  
```  
<RSSharePointList>  
<listName>Tasks</listName>  
</RSSharePointList>  
```  
  
 在查詢結果中，會傳回 Tasks 清單的所有欄位。  
  
##  <a name="Parameters"></a> 參數  
 此資料延伸模組不支援參數。  
  
  
##  <a name="HowTo"></a> 如何主題  
 本節包含使用資料連接、資料來源與資料集的逐步指示。  
  
 [加入及驗證資料連接或資料來源&#40;報表產生器及 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [建立共用資料集或內嵌資料集 &#40;報表產生器及 SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [將篩選加入資料集中 &#40;報表產生器及 SSRS&#41;](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="Related"></a> 相關章節  
 本文件集的這些章節會提供報表資料的深入概念性資訊，以及如何定義、自訂和使用與報表資料相關組件的程序資訊。  
  
 [將資料加入至報表&#40;報表產生器及 SSRS&#41;](report-datasets-ssrs.md)  
 提供存取報表資料的概觀。  
  
 [報表產生器中的資料連接、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 提供資料連接與資料來源的相關資訊。  
  
 [報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 提供內嵌與共用資料集的相關資訊。  
  
 [資料集欄位集合 &#40;報表產生器及 SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)  
 提供查詢所產生之資料集欄位集合的相關資訊。  
  
 《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [線上叢書》](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文件的 [Reporting Services 支援的資料來源 &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)。  
 提供支援每一個資料延伸模組之平台與版本的深入資訊。  
  
  
## <a name="see-also"></a>另請參閱  
 [報表參數 &#40;報表產生器和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [運算式 &#40;報表產生器及 SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
