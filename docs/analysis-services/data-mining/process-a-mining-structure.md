---
title: 處理採礦結構 |Microsoft 文件
ms.custom: ''
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], processing
ms.assetid: 4162f33e-c23f-4293-8905-271781e45fa4
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d5b44aa20952d938f0f2012ae89e7ab6b8046e98
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="process-a-mining-structure"></a>處理採礦結構
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  在您可以瀏覽或使用與採礦結構相關聯的採礦模型之前，必須部署 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案並處理採礦結構和採礦模型。 此外，如果您變更採礦結構或採礦模型，會提示您重新部署和處理它們。 在 **中之資料採礦設計師的** [採礦結構] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 索引標籤中處理結構時，會處理所有相關聯的模型。  
  
 您可以使用下列工具來處理採礦結構：  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   XMLA：處理命令  
  
 如需如何處理個別模型的資訊，請參閱 [處理採礦模型](../../analysis-services/data-mining/process-a-mining-model.md)。  
  
### <a name="to-process-a-mining-structure-and-all-associated-mining-models-using-sql-server-data-tools"></a>若要使用 SQL Server 資料工具來處理採礦結構和所有相關聯的採礦模型  
  
1.  從 **中的** [採礦模型] **功能表項目選取** [處理採礦結構和所有模型] [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]。  
  
     如果您變更了結構，在處理模型之前，會提示您重新部署結構。 按一下 **[是]**。  
  
2.  按一下**執行**中**處理採礦結構 –\<結構 >**  對話方塊。  
  
     隨即開啟 **[處理進度]** 對話方塊，以顯示模型處理的詳細資料。  
  
3.  在模型完成處理之後，按一下 **[處理進度]** 對話方塊中的 **[關閉]** 。  
  
4.  按一下**關閉**中**處理採礦結構 –\<結構 >**  對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [採礦結構工作和使用說明](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
