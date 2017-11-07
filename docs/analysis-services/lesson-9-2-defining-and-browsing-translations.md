---
title: "定義和瀏覽翻譯 |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 0e60be99-3768-499c-a22c-a4ec37e61887
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c7d55390b1d27fb595b139c06d9dd45b24737522
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-9-2---defining-and-browsing-translations"></a>課程 9-2-定義和瀏覽翻譯
翻譯是指採用特定語言之 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件名稱的表示。 這些物件包括量值群組、量值、維度、屬性、階層、KPI、動作和導出成員。 翻譯會針對可支援多種語言的用戶端應用程式，提供伺服器支援。 透過使用這類用戶端，用戶端會將地區設定識別碼 (LCID) 傳遞給 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的執行個體，然後當它提供 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件的中繼資料時，就會使用此 LCID 來決定要使用哪一組翻譯。 如果 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件沒有包含該語言的翻譯，或者沒有包含指定之物件的翻譯，則在將物件中繼資料傳回到用戶端時會使用預設語言。 例如，假設有一位法國的商務使用者從地區設定為法文的工作站中存取 Cube，若有法文翻譯的話，則該商務使用者會看到法文的成員標題及成員屬性值。 不過，如果位於德國的商務使用者，從具有德文地區設定的工作站存取同一個 Cube，商務使用者就會看到德文的標題名稱以及成員屬性值。 如需詳細資訊，請參閱 [維度翻譯](../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)、 [Cube 翻譯](../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md)和 [Analysis Services 中的翻譯支援](../analysis-services/translation-support-in-analysis-services.md)。  
  
在這個主題的工作中，您會在 [日期] 維度中，為一組有限的維度物件集定義中繼資料翻譯，以及在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 中，為 Cube 物件定義中繼資料翻譯。 您會瀏覽這些維度和 Cube 物件，來檢查中繼資料翻譯。  
  
## <a name="specifying-translations-for-the-date-dimension-metadata"></a>指定日期維度中繼資料的翻譯  
  
1.  開啟適用於 [日期] 維度的維度設計師，然後按一下 [翻譯] 索引標籤。  
  
    此時會出現每一個維度物件以預設語言表示的中繼資料。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 的預設語言是英文。  
  
2.  在 [翻譯] 索引標籤的工具列上，按一下 [新增翻譯] 按鈕。  
  
    [選取語言] 對話方塊中會顯示一份語言清單。  
  
3.  按一下 [西班牙文 (西班牙)]，然後按一下 [確定]。  
  
    此時會出現新的資料行，讓您針對您要翻譯的中繼資料物件，定義西班牙文翻譯。 在這個教學課程中，我們只會翻譯少量的物件來示範此程序。  
  
4.  在 [翻譯] 索引標籤的工具列上，按一下 [新增翻譯] 按鈕，並在 [選取語言] 對話方塊中按一下 [法文 (法國)]，然後按一下 [確定]。  
  
    此時會出現另一個語言資料行，讓您定義法文翻譯。  
  
5.  在 [日期] 維度的 [標題] 物件資料列中，在 [西班牙文 (西班牙)] 翻譯資料行輸入 **Fecha**，然後在 [法文 (法國)] 翻譯資料行輸入 **Temps**。  
  
6.  在 [月份名稱] 屬性的 [標題] 物件資料列中，在 [西班牙文 (西班牙)] 翻譯資料行輸入 **Mes del Año**，然後在 [法文 (法國)] 翻譯資料行輸入 **Mois d'Année**。  
  
    請注意，當您輸入這些翻譯時，會出現省略符號 (**…**)。 按一下這個省略符號，可讓您在基礎資料表中指定一個資料行，以便提供屬性階層每個成員的翻譯。  
  
7.  按一下 [月份名稱] 屬性的 [西班牙文 (西班牙)] 翻譯的省略符號 (**…**)。  
  
    此時會出現 [屬性資料翻譯] 對話方塊。  
  
8.  在 [翻譯資料行] 清單中選取 **SpanishMonthName**，如下圖所示。  
  
    ![屬性資料翻譯對話方塊](../analysis-services/media/l9-translations-4.gif "屬性資料翻譯對話方塊")  
  
9. 按一下 [確定]，然後按一下 [月份名稱] 屬性的 [法文 (法國)] 翻譯的省略符號 (**…**)。  
  
10. 在 翻譯資料行 清單中選取 **FrenchMonthName**，然後按一下 確定。  
  
    這個處理序的步驟，主要在示範如何定義維度物件和成員的中繼資料翻譯。  
  
## <a name="specifying-translations-for-the-analysis-services-tutorial-cube-metadata"></a>指定 Analysis Services 教學課程 Cube 中繼資料的翻譯  
  
1.  切換到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 的 Cube 設計師，然後再切換到 [翻譯] 索引標籤。  
  
    此時會出現每一個 Cube 物件以預設語言表示的中繼資料，如下圖所示。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 的預設語言是英文。  
  
    ![預設語言翻譯索引標籤中](../analysis-services/media/l9-translations-5.gif "預設語言翻譯索引標籤中")  
  
2.  在 [翻譯] 索引標籤的工具列上，按一下 [新增翻譯] 按鈕。  
  
    [選取語言] 對話方塊中會顯示一份語言清單。  
  
3.  選取 [西班牙文 (西班牙)]，然後按一下 [確定]。  
  
    此時會出現新的資料行，讓您針對您要翻譯的中繼資料物件，定義西班牙文翻譯。 在這個教學課程中，我們只會翻譯少量的物件來示範此程序。  
  
4.  在 [翻譯] 索引標籤的工具列上，按一下 [新增翻譯] 按鈕，並選取 [選取語言] 對話方塊中的 [法文 (法國)]，然後按一下 [確定]。  
  
    此時會出現另一個語言資料行，讓您定義法文翻譯。  
  
5.  在 [日期] 維度的 [標題] 物件資料列中，在 [西班牙文 (西班牙)] 翻譯資料行輸入 **Fecha**，然後在 [法文 (法國)] 翻譯資料行輸入 **Temps**。  
  
6.  在 [網際網路銷售] 量值群組的 [標題] 物件資料列中，在 [西班牙文 (西班牙)] 翻譯資料行輸入 **Ventas del lnternet**，然後在 [法文 (法國)] 翻譯資料行輸入 **Ventes D'Internet**。  
  
7.  在 [Internet Sales-Sales Amount (網際網路銷售 - 銷售量)] 量值的 [標題] 物件資料列中，在 [西班牙文 (西班牙)] 翻譯資料行輸入 **Cantidad de las Ventas del Internet**，然後在 [法文 (法國)] 翻譯資料行輸入 **Quantité de Ventes d'Internet**。  
  
    這個處理序的步驟，主要在示範如何定義 Cube 物件的中繼資料翻譯。  
  
## <a name="browsing-the-cube-by-using-translations"></a>利用翻譯來瀏覽 Cube  
  
1.  在 [建立] 功能表上，按一下 [Deploy Analysis Services Tutorial (部署 Analysis Services Tutorial)]。  
  
2.  順利完成部署之後，切換到 [瀏覽器] 索引標籤，然後按一下 [重新連接]。  
  
3.  從 [資料] 窗格中移除所有階層和量值，然後在 [檢視方塊] 清單中選取 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程。  
  
4.  在 [中繼資料] 窗格中，展開 [量值]，然後再展開 [網際網路銷售]。  
  
    請注意，[Internet Sales-Sales Amount (網際網路銷售 - 銷售量)] 量值會以英文出現在這個量值群組中。  
  
5.  在工具列上，選取 [語言] 清單中的 [西班牙文 (西班牙)]。  
  
    請注意，[中繼資料] 窗格中的項目會重新擴展。 [中繼資料] 窗格中的項目重新擴展之後，請注意，[網際網路銷售 - 銷售量] 量值就不會出現在 [網際網路銷售] 顯示資料夾中了， 而是以西班牙文顯示在另一個名叫 **Ventas del lnternet**的新顯示資料夾中，如下圖所示。  
  
    ![Repopulated 中繼資料 窗格](../analysis-services/media/l9-translations-6.gif "Repopulated 中繼資料 窗格")  
  
6.  在 [中繼資料] 窗格中，以滑鼠右鍵按一下 [Cantidad de las Ventas del Internet]，然後選取 [加入至查詢]。  
  
7.  在 [中繼資料] 窗格中，依序展開 [Fecha] 和 [Fecha.Calendar Date]，再以滑鼠右鍵按一下 [Fecha.Calendar Date]，然後選取 [加入至篩選]。  
  
8.  在 [篩選] 窗格中，選取 [CY 2007] 做為篩選運算式。  
  
9. 在 [中繼資料] 窗格中，以滑鼠右鍵按一下 [Mes del Ano]，然後選取[加入至查詢]。  
  
    請注意，月份是以西班牙文顯示，如下圖所示。  
  
    ![在資料窗格中的西班牙文月份名稱](../analysis-services/media/l9-translations-7.gif "資料窗格中的，以西班牙文月份名稱")  
  
10. 在工具列上，選取 [語言] 清單中的 [法文 (法國)]。  
  
    請注意，現在月份會以法文顯示，與量值名稱一樣。  
  
## <a name="next-lesson"></a>下一課  
[第 10 課：定義管理角色](../analysis-services/lesson-10-defining-administrative-roles.md)  
  
## <a name="see-also"></a>另請參閱  
[維度翻譯](../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)  
[Cube 翻譯](../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md)  
[Analysis Services 中的翻譯支援](../analysis-services/translation-support-in-analysis-services.md)  
  
  
  

