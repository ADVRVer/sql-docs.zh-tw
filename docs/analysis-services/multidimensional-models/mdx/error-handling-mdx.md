---
title: "錯誤處理 (MDX) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8679c6d912e6dab8fa89f4f67ddfa9070c04460f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="error-handling-mdx"></a>錯誤處理 (MDX)
  每個 Cube 都可以控制多維度運算式 (MDX) 指令碼內錯誤的處理方式。 透過 **ScriptErrorHandlingMode** 列舉值便可完成錯誤處理。 此列舉值可能出現的值如下：  
  
 **IgnoreNone**  
 當 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 發現 MDX 指令碼中有任何錯誤時，可導致伺服器引發錯誤。  
  
 **IgnoreAll**  
 使伺服器忽略 MDX 指令碼中內含錯誤的所有命令，包括語法錯誤、名稱解析錯誤等等。  
  
## <a name="see-also"></a>請參閱＜  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
