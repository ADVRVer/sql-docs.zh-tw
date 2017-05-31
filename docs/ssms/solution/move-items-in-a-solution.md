---
title: "移動方案中的項目 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- moving items
- solutions [SQL Server Management Studio], item relocation
- relocating items
ms.assetid: b40a24eb-f528-4e70-b26e-5eaf6e0ed1ed
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b0140646e92871aa5d3ab2acbb95b417ab38d28b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/11/2017

---
# <a name="move-items-in-a-solution"></a>移動方案中的項目
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] 專案中的專案項目有「查詢」、「連接」及「其他」檔案。 您可以在 [方案總管] 中的各專案之間移動「查詢」和「其他」檔案，不過，不能移動「連接」。  
  
### <a name="to-move-items-in-solution-explorer"></a>在 [方案總管] 中移動項目  
  
1.  在 [方案總管] 中，選取您要移動的項目。  
  
2.  在 [編輯] 功能表上，按一下 [剪下]。  
  
3.  在 [方案總管] 中，選取目的地。  
  
4.  在 [編輯] 功能表上，按一下 [貼上]。  
  
您可以在 [方案總管] 內拖曳「查詢」和「其他」檔案來移動項目。 拖曳可讓您查看拖曳作業的結果。 在專案類型之間移動查詢，可能會造成在目標專案中，將查詢視為其他檔案。  
  
> [!NOTE]  
> 移動連接的查詢，並不會將連接移到目標專案中。 在查詢移到目標專案之後，查詢會失去它的連接。  
  
## <a name="see-also"></a>另請參閱  
[方案總管](../../ssms/solution/solution-explorer.md)  
[複製方案中的項目](../../ssms/solution/copy-items-in-a-solution.md)  
  

