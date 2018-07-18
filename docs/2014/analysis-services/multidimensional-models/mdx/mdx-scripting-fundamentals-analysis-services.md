---
title: MDX 指令碼基礎觀念 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], scripts
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [MDX]
- cubes [Analysis Services], calculations
- Multidimensional Expressions [Analysis Services], scripts
ms.assetid: fdecb3ce-7c87-4bab-8000-532ba7a29f96
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 01f105ab8cd05029ac4dc7d747f5b0c016745962
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37325188"
---
# <a name="mdx-scripting-fundamentals-analysis-services"></a>MDX 指令碼基礎觀念 (Analysis Services)
  在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]中，多維度運算式 (MDX) 指令碼是由一或多個 MDX 運算式或陳述式構成，利用計算擴展 Cube。  
  
 MDX 指令碼可定義 Cube 的計算處理序。 MDX 指令碼也會被視為 Cube 本身的一部分。 因此，變更與 Cube 相關的 MDX 指令碼，會立即變更 Cube 的計算處理序。  
  
 若要建立 MDX 指令碼，您可以使用 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中的 Cube 設計師。 如需詳細資訊，請參閱 [定義指派和其他指令碼命令](../define-assignments-and-other-script-commands.md) [Introduction to MDX Scripting in Microsoft SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81892)(Microsoft SQL Server 2005 中 MDX 指令碼的簡介)。  
  
 如需 MDX 查詢和計算的效能相關問題，請參閱 [SQL Server Analysis Services Performance Guide](http://go.microsoft.com/fwlink/p/?LinkId=399050)(SQL Server Analysis Services 效能指南) 中的＜MDX optimization (MDX 最佳化)＞一節。  
  
## <a name="in-this-section"></a>本節內容  
  
|主題|描述|  
|-----------|-----------------|  
|[基本 MDX 指令碼&#40;MDX&#41;](the-basic-mdx-script-mdx.md)|詳細說明基本的 MDX 指令碼，包括每個 Cube 提供的預設 MDX 指令碼，以及在 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]中，MDX 指令碼一般會如何在 Cube 內運作。|  
|[管理範圍及內容&#40;MDX&#41;](managing-scope-and-context-mdx.md)|描述如何使用 [CALCULATE](/sql/mdx/mdx-scripting-calculate) 陳述式、[SCOPE](/sql/mdx/mdx-scripting-scope) 陳述式及 [This](/sql/mdx/this-mdx) 函數，管理 MDX 指令碼內的內容與範圍。|  
|[使用變數與參數&#40;MDX&#41;](using-variables-and-parameters-mdx.md)|描述如何使用 MDX 指令碼中的變數與參數。|  
|[錯誤處理&#40;MDX&#41;](error-handling-mdx.md)|說明 MDX 指令碼內的錯誤處理。|  
|[支援 MDX &#40;MDX&#41;](supported-mdx-mdx.md)|提供 MDX 指令碼內支援的 MDX 運算子、陳述式及函數的清單。|  
  
## <a name="see-also"></a>另請參閱  
 [MDX 語言參考&#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx)  
  
  
