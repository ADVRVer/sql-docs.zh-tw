---
title: "資料清理 | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2012"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e67136cc-f8c6-4cb3-ba0b-c966c636256c
caps.latest.revision: 31
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 31
---
# 資料清理
  資料清理是分析資料來源中的資料品質、手動核准/拒絕系統的建議，藉以對資料進行變更的程序。 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中的資料清理包含電腦輔助的程序，以分析資料符合知識庫中知識的方式，同時也包含一個互動式程序，讓資料管理人檢閱並修改電腦輔助的程序結果，以確保資料清理完全符合其希望的執行方式。  
  
 資料管理人也可以在 Integration Services 封裝程序中執行資料清理。 在此情況下，資料管理人會使用 [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]，透過現有的知識庫自動執行資料清理。 如需詳細資訊，請參閱 [DQS 清理轉換](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)。  
  
 DQS 中的資料清理功能具有下列優點：  
  
-   識別資料來源 (Excel 檔案或 SQL Server 資料庫) 中不完整或不正確的資料，然後更正無效的資料或向您發出相關警示。  
  
-   提供兩個步驟的程序來清理資料︰ *電腦輔助* 和 *互動式*。 電腦輔助的程序會使用 DQS 知識庫中的知識自動處理資料，並建議替代項目/更正。 下一個步驟是互動式程序，可讓資料管理人核准、拒絕或修改 DQS 在電腦輔助的清理期間所提議的變更。  
  
-   使用定義域值、定義域規則和參考資料，標準化並充實客戶資料。 例如，透過將 “St.” 變更為 “Street” 讓詞彙使用方式標準化， 並透過將 “1 Microsoft way Redmond 98006” 變更為 “1 Microsoft Way, Redmond, WA 98006” 來填入遺漏的元素，藉以豐富資料。  
  
-   為使用者提供簡單、直覺，以及類似精靈的一致介面，以便在一組非常大的資料之間瀏覽資料並檢查其中的錯誤。  
  
 下圖顯示如何在 DQS 中進行資料清理：  
  
 ![DQS 中的資料清理程序](../data-quality-services/media/dqs-cleansingprocess.gif "DQS 中的資料清理程序")  
  
##  <a name="ComputerAssisted"></a> 電腦輔助的清理  
 DQS 資料清理程序會將知識庫套用至要清理的資料，以及建議資料變更。 資料服務員可以存取每個建議變更，以評估及更正變更。 若要執行資料清理，資料管理人要依下列程序進行：  
  
1.  建立資料品質專案中，選取知識庫，針對您想要分析並清理來源資料，然後選取 **清理** 活動。 多個資料品質專案可以使用相同的知識庫。  
  
2.  指定資料庫資料表/檢視表，或包含要清理之來源資料的 Excel 檔案。 資料庫或 Excel 檔案都可以是用於知識探索的相同資料庫，或是不同的資料庫或 Excel 檔案。  
  
    > [!NOTE]  
    >  如果您為知識探索與清理活動選取相同的資料來源，資料將不會有變更。 建議您針對範例資料執行知識探索，之後再針對在知識探索活動期間建立的知識，清理資料來源。  
  
3.  將要清理的資料欄位對應到知識庫中適當的定義域/複合定義域。 如果您將某個欄位對應到複合定義域，則會在欄位和複合定義域之間發生對應，而且不會與複合定義域中的個別定義域對應。 此外，系統會根據針對複合定義域指定的規則，完成已對應欄位的資料清理，而且不會針對複合定義域中的個別定義域進行。 如需有關複合定義域的詳細資訊，請參閱 [DQS 知識庫與定義域](../data-quality-services/dqs-knowledge-bases-and-domains.md)。  
  
4.  執行電腦輔助的清理程序，藉以 **啟動** 上 **清理** 頁面。  
  
 資料清理程序會尋找最符合已知資料定義域值的資料執行個體。 此程序會將資料品質知識套用至所有來源資料，不像知識探索程序只針對範例資料的百分比執行。  
  
 電腦輔助的程序會在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 中顯示資料品質資訊，供互動式清理程序使用。 除了遵循語法錯誤規則，DQS 也使用參考資料和進階的演算法將使用的資料分類 *信賴等級*。 信賴等級表示 DQS 對更正或建議的確定程度。 信賴等級以下列臨界值為基礎：  
  
-    *自動更正臨界值* 值高於此 DQS 會建議變更，除非資料管理人拒絕否則進行。 您可以在 **[組態]** 畫面的 **[一般設定]** 索引標籤中，指定自動更正臨界值。 如需詳細資訊，請參閱 [Configure Threshold Values for Cleansing and Matching](../data-quality-services/configure-threshold-values-for-cleansing-and-matching.md)。  
  
-    *自動建議臨界值* 低於自動更正臨界值，高於此 DQS 會建議變更，如果資料管理人核准則進行的值。 您可以在 **[組態]** 畫面的 **[一般設定]** 索引標籤中，指定自動建議臨界值。 如需詳細資訊，請參閱 [Configure Threshold Values for Cleansing and Matching](../data-quality-services/configure-threshold-values-for-cleansing-and-matching.md)。  
  
 DQS 會將信賴等級低於自動建議臨界值的任何值保持原狀 (除非資料管理人指定變更)。  
  
##  <a name="Interactive"></a> 互動式清理  
 根據電腦輔助的清理程序，DQS 會為資料管理人提供決定變更資料所需的資訊。 DQS 會將資料分類成下列五個索引標籤：  
  
-   **建議**︰ 哪些 Dqs 找到信賴等級高於的建議 *自動建議臨界值* 但低於 *自動更正臨界值* 值。 您應該檢閱這些值並且適當核准或拒絕。  
  
-   **新**: DQS 沒有足夠的資訊 （建議），且因此無法對應至任何其他索引標籤的有效值。 此外，此索引標籤也包含信賴等級的值小於 *自動建議臨界值* 值，但夠高而可以標示為有效。  
  
-   **無效**︰ 標示為無效的知識庫或定義域規則或參考資料的值在網域中的值。 此索引標籤也將包含使用者在互動式清理程序期間，於其他四個索引標籤中任一個索引標籤中拒絕的值。  
  
-   **已更正**: DQS 找到信賴等級上述值的更正時在自動清理 DQS 更正的值處理 *自動更正臨界值* 值。 此索引標籤也將包含使用者指定正確的值中的值 **更正為** 資料行在互動式清理，然後等待中的選項按鈕，即可核准 **核准** 任何其他四個索引標籤中的資料行。  
  
-   **正確**︰ 找不到正確的值。 例如，值符合定義域值。 如有需要，您可以覆寫 DQS 清理拒絕此索引標籤下的值或指定替代的文字中 **更正為** 資料行，然後按一下 [選項按鈕，在 **接受** 資料行。 此索引標籤也會包含已核准的使用者，在按一下選項按鈕，在互動式清理期間的值 **核准** 中的資料行 **新增** 或 **無效** ] 索引標籤。  
  
> [!NOTE]  
>  在 **建議**, ，**更正**, ，和 **更正** 索引標籤上，DQS 會顯示網域的前置值如果適用的話，在 **更正為** 針對個別的定義域值的資料行。  
  
 資料管理人會使用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 查看 DQS 建議的變更，以及決定是否實作變更。 他可以確認 DQS 已指定為正確的值，實際上是正確的。 他可以確認應該進行 DQS 以高信賴等級所做的變更。 他可以決定是否核准自動建議的變更。 而且他可以檢閱尚未變更的值，以便進行電腦輔助程序未發現的變更。  
  
 DQS 會將資料管理人所做的任何變更與電腦輔助資料清理結果合併。 這些變更會保存在專案中，但不會加入至知識庫。 在資料清理期間，相關聯的知識庫是唯讀的。  
  
 當資料清理程序完成時，您可以選擇將已處理的資料匯出至 SQL Server 資料庫中的新資料表 (.csv 檔案或 Excel 檔案)。 執行清理的來源資料會保持其原始狀態。 資料服務員可以使用個別的清理資料來更正實際的來源資料。  
  
 下圖顯示如何使用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 應用程式進行資料清理：  
  
 ![Data Quality Client 中的資料清理](../data-quality-services/media/dqs-cleansingindqsclient.gif "Data Quality Client 中的資料清理")  
  
##  <a name="Leading"></a> 前置值更正  
 前置值更正適用於擁有同義字，而且使用者想要使用其中一個同義字值做為前置值 (而非表示一致值的其他值) 的定義域值。 例如，“New York”、“NYC” 和 “big apple” 是同義字，而且使用者想要使用 “New York” 做為前置值，而非 “NYC” 和 “Big Apple”。 DQS 在清理程序期間支援前置值更正，以協助您將資料標準化。 只有在針對建立定義域時啟用成相同的定義域，才會進行前置值更正。 根據預設，針對前置值更正，除非您清除 [啟用所有定義域 **使用前置值** 建立定義域時核取方塊。 如需有關此核取方塊的詳細資訊，請參閱 [設定網域屬性](../data-quality-services/set-domain-properties.md)。  
  
##  <a name="Standardize"></a> 標準化清理的資料  
 您可以選擇是否要根據針對定義域所定義的輸出格式，以標準化格式匯出已清理的資料。 建立定義域時，您可以選取當定義域中的資料值為輸出時，將套用的格式。 如需指定網域的輸出格式的詳細資訊，請參閱 **輸出格式為** 清單中 [設定網域屬性](../data-quality-services/set-domain-properties.md)。  
  
 在 [匯出已清理的資料時 **匯出** 頁面中清理資料品質專案精靈，您指定是否要選取，以標準化格式匯出已清理的資料 **標準化輸出** 核取方塊。 根據預設，已清理的資料會以標準化格式匯出，亦即，選取該核取方塊。 如需有關匯出已清理的資料的詳細資訊，請參閱 [使用 DQS 清理資料 #40，供內部使用 & #41;知識](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)。  
  
##  <a name="Related"></a> 相關工作  
  
|工作描述|主題|  
|----------------------|-----------|  
|描述如何設定清理活動的臨界值。|[Configure Threshold Values for Cleansing and Matching](../data-quality-services/configure-threshold-values-for-cleansing-and-matching.md)|  
|描述如何使用內建到 DQS 中的知識清理資料。|[使用 DQS & #40; 清理資料內部 & #41;知識](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)|  
|描述如何使用 Reference Data Service 中的知識清理資料。|[使用參考資料和 #40; 清理資料外部 & #41;知識](../data-quality-services/cleanse-data-using-reference-data-external-knowledge.md)|  
|描述如何清理複合定義域。|[清理複合定義域中的資料](../data-quality-services/cleanse-data-in-a-composite-domain.md)|  
  
## 另請參閱  
 [資料品質專案 #40; DQS & #41;](../data-quality-services/data-quality-projects-dqs.md)   
 [資料比對](../data-quality-services/data-matching.md)  
  
  