---
title: 使用聯集全部轉換來合併資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- merging datasets [Integration Services]
- merging inputs [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 78304403-a81c-4101-b87e-ec80ddfdac98
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7f5504c6f58d7ff5254d081ea479ca30ed6ca705
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62770335"
---
# <a name="merge-data-by-using-the-union-all-transformation"></a>使用聯集全部轉換來合併資料
  若要加入及設定「聯集全部」轉換，封裝必須已包括至少一個「資料流程」工作與兩個資料來源。  
  
 「聯集全部」轉換可合併多個輸入。 連接到轉換的第一個輸入為參考輸入，隨後連接的輸入為次要輸入。 輸出包括參考輸入中的資料行。  
  
### <a name="to-combine-inputs-in-a-data-flow"></a>將輸入合併於資料流程  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中，按兩下方案總管中的封裝，以在 [[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師] 中開啟封裝，然後按一下 [資料流程] 索引標籤。  
  
2.  將「聯集全部」轉換從 [工具箱] 拖曳至 [資料流程] 索引標籤的設計介面。  
  
3.  將連接子從資料來源或前一個轉換拖曳至「聯集全部」轉換，以便將「聯集全部」轉換連接到資料流程。  
  
4.  按兩下 [聯集全部] 轉換。  
  
5.  在 [聯集全部轉換編輯器] 中，藉由按一下資料列並選取輸入清單中的資料行，將輸入的資料行對應至 [輸出資料行名稱] 清單中的資料行。 選取輸入清單中的 [\<忽略>]，以略過資料行的對應。  
  
    > [!NOTE]  
    >  兩個資料行之間的對應，會要求資料行的中繼資料相符。  
  
    > [!NOTE]  
    >  未對應至參考資料行之次要輸入中的資料行，在輸出中會設為 Null 值。  
  
6.  (選擇性) 在 [輸出資料行名稱] 資料行中修改資料行的名稱。  
  
7.  針對每個輸入中的每個資料行重複步驟 5 與 6。  
  
8.  按一下 [確定] 。  
  
9. 若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。  
  
## <a name="see-also"></a>另請參閱  
 [Union All Transformation](union-all-transformation.md)   
 [Integration Services 轉換](integration-services-transformations.md)   
 [Integration Services 路徑](../integration-services-paths.md)   
 [資料流程工作](../../control-flow/data-flow-task.md)  
  
  
