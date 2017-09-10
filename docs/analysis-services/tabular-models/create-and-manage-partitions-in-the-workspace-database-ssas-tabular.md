---
title: "建立及管理工作空間資料庫 (SSAS 表格式) 中的資料分割 |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.partitionmgr.f1
ms.assetid: 0b3027d6-652b-4eb3-a197-58b25df65218
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 737b5220666edbbb481f0e50671b65e5a55a1de5
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="create-and-manage-partitions-in-the-workspace-database-ssas-tabular"></a>在工作空間資料庫中建立及管理資料分割 (SSAS 表格式)
  分割區會將一個資料表分割成多個邏輯部分。 每個資料分割可以不受其他資料分割的影響，單獨處理 (重新整理) 或平行處理。 資料分割可以改善大型資料庫的可調適性和管理能力。 依預設，每個資料表都包含一個資料分割，其中包含所有資料行。 本主題中的工作說明如何使用 **中的** [資料分割管理員] [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]  
  
 將模型部署至其他 Analysis Services 執行個體之後，資料庫管理員即可使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]來建立及管理 (已部署) 模型中的資料分割。 如需詳細資訊，請參閱[建立及管理表格式模型資料分割 &#40;SSAS 表格式&#41;](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)。  
  
 本主題也包括下列工作：  
  
-   [建立新的資料分割](#bkmk_create_new)  
  
-   [複製資料分割](#bkmk_copy)  
  
-   [若要刪除資料分割](#bkmk_delete)  
  
> [!NOTE]  
>  您不能使用 [資料分割管理員] 對話方塊，來合併模型工作空間資料庫中的資料分割。 資料分割只能透過使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，在已部署的模型中合併。  
  
## <a name="tasks"></a>工作  
 若要建立和管理資料分割，您要使用 **[資料分割管理員]** 對話方塊。 若要檢視 **[資料分割管理員]** 對話方塊，請在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，按一下 **[資料表]** 功能表，然後按一下 **[資料分割]**。  
  
###  <a name="bkmk_create_new"></a> 建立新的資料分割  
  
1.  在模型設計師中，選取您要定義資料分割的資料表。  
  
2.  按一下 **[資料表]** 功能表，然後按一下 **[資料分割]**。  
  
3.  在 **[資料分割管理員]**的 **[資料表]** 清單方塊中，確認或選取要資料分割的資料表，然後按一下 **[新增]**。  
  
4.  在 **[資料分割名稱]**中，輸入資料分割的名稱。 依預設，每個新資料分割的預設資料分割名稱是以累加的方式進行編號。  
  
5.  您可使用資料表預覽模式或使用查詢編輯器模式所建立的 SQL 查詢，選取資料分割中要包含的資料列及資料行。  
  
     若要使用資料表預覽模式 (預設值)，請按一下預覽視窗右上角附近的 [資料表預覽] 按鈕。 選取資料行名稱旁邊的核取方塊，即可選取要加入資料分割的資料行。 若要篩選資料列，請以滑鼠右鍵按一下資料格值，然後按一下 **[依選取的資料格值篩選]**。  
  
     若要使用 SQL 陳述式，請按一下預覽視窗右上角附近的 [查詢編輯器] 按鈕，然後將 SQL 查詢陳述式輸入或貼到查詢視窗中。 若要驗證您的陳述式，請按一下 **[驗證]**。 若要使用查詢設計工具，請按一下 **[設計]**。  
  
###  <a name="bkmk_copy"></a> 複製資料分割  
  
1.  在 **[資料分割管理員]**的 **[資料表]** 清單方塊中，確認或選取含有要複製之資料分割的資料表。  
  
2.  在 **[資料分割]** 清單中，選取要複製的資料分割，然後按一下 **[複製]**。  
  
3.  在 **[資料分割名稱]**中，輸入資料分割的新名稱。  
  
###  <a name="bkmk_delete"></a> 若要刪除資料分割  
  
1.  在 **[資料分割管理員]**的 **[資料表]** 清單方塊中，確認或選取含有要刪除之資料分割的資料表。  
  
2.  在 **[資料分割]** 清單中，選取要刪除的資料分割，然後按一下 **[刪除]**。  
  
## <a name="see-also"></a>請參閱＜  
 [資料分割 &#40;SSAS 表格式&#41;](../../analysis-services/tabular-models/partitions-ssas-tabular.md)   
 [在工作空間資料庫中處理資料分割 &#40;SSAS 表格式&#41;](../../analysis-services/tabular-models/process-partitions-in-the-workspace-databse-ssas-tabular.md)  
  
  
