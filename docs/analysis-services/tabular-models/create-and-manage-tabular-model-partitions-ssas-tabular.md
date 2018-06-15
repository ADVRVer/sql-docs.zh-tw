---
title: 建立及管理表格式模型資料分割 |Microsoft 文件
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7067449c0de9958e98a7a9dc5cc09c7f89f33fa9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34039883"
---
# <a name="create-and-manage-tabular-model-partitions"></a>建立及管理表格式模型資料分割
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  分割區會將一個資料表分割成多個邏輯部分。 接著，每個分割區可以不受其他分割區的影響，單獨處理 (重新整理)。 模型撰寫期間，在已部署的模型中有重複定義的模型資料分割。 部署之後，即可使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的 [資料分割] 對話方塊或指令碼，管理這些資料分割。 此主題提供的工作描述如何為已部署的模型建立及管理資料分割。  
  
  > [!NOTE]  
>  建立 1400年相容性層級的表格式模型中的資料分割會定義使用 M 查詢陳述式。 若要進一步了解，請參閱[M 參考](https://msdn.microsoft.com/library/mt211003.aspx)。 
>
  
## <a name="tasks"></a>工作  
 若要為已部署的表格式模型資料庫建立及管理資料分割，您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的 [資料分割] 對話方塊。 若要檢視 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [資料分割] 對話方塊，請以滑鼠右鍵按一下資料表，然後按一下 [資料分割]。  
  
###  <a name="bkmk_create_new"></a> 建立新的資料分割  
  
1.  在 [資料分割] 對話方塊中，按一下 [新增] 按鈕。  
  
2.  在 **[資料分割名稱]** 中，輸入資料分割的名稱。 依預設，每個新資料分割的預設資料分割名稱是以累加的方式進行編號。  
  
3.  在**查詢陳述式**、 輸入或貼上資料行和任何您想要加入資料分割到查詢視窗的子句會定義 SQL 或 M 查詢陳述式。  
  
4.  若要驗證陳述式，請按一下 [檢查語法]。  
  
###  <a name="bkmk_copy"></a> 複製資料分割  
  
1.  在 [資料分割] 對話方塊的 [資料分割] 清單中，選取您要複製的資料分割，然後按一下 [複製] 按鈕。  
  
2.  在 **[資料分割名稱]** 中，輸入資料分割的新名稱。  
  
3.  在**查詢陳述式**，編輯查詢陳述式。  
  
###  <a name="bkmk_merge"></a> 合併兩個或兩個以上的資料分割  
  
-   在**資料分割**對話方塊中，於**資料分割**清單，使用 Ctrl + 按一下以選取您想要合併的資料分割，然後按一下**合併** 按鈕。  
  
> [!IMPORTANT]  
>  合併資料分割並不會更新資料分割中繼資料。 您必須編輯 SQL 或 M 陳述式結果的資料分割，以確定處理作業會處理合併的資料分割中的所有資料。  
  
###  <a name="bkmk_delete"></a> 若要刪除資料分割  
  
-   在 [資料分割] 對話方塊的 [資料分割] 清單中，選取您要刪除的資料分割，然後按一下 [刪除] 按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [表格式模型資料分割](../../analysis-services/tabular-models/tabular-model-partitions-ssas-tabular.md)   
 [處理表格式模型資料分割](../../analysis-services/tabular-models/process-tabular-model-partitions-ssas-tabular.md)  
  
  
