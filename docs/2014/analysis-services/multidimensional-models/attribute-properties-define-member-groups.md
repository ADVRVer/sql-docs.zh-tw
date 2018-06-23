---
title: 定義成員群組 |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- member groups [Analysis Services]
- grouping members
- DiscretizationMethod property
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7b9daa1b369f1d42a4dbaea76060bdefe6741a18
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36136749"
---
# <a name="define-member-groups"></a>定義成員群組
  如果屬性有大量成員，您可以選擇將這些成員分組成值區，減少使用者在階層中瀏覽資料時所看到的成員數目。 您也可以決定成員分組的值區數目和設定值區的命名配置。 如需詳細資訊，請參閱 [Group Attribute Members &#40;Discretization&#41;](attribute-properties-group-attribute-members.md) (群組屬性成員 (分隔))。  
  
 您可藉由設定 **[DiscretizationMethod]** 屬性來群組成員，這個屬性是透過 **中的** [屬性] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]視窗來加以存取。  
  
 當您建立成員群組時，要等到您處理該維度之後，使用者才能看到您所做的變更。 如需詳細資訊，請參閱[多維度模型物件處理](processing-a-multidimensional-model-analysis-services.md)。  
  
### <a name="to-create-member-groups"></a>若要建立成員群組  
  
1.  開啟您要使用的維度。 依預設，會開啟 **[維度結構]** 索引標籤。  
  
2.  在 [屬性] 中，以滑鼠右鍵按一下您要將其成員分組的屬性，然後按一下 [屬性]。  
  
3.  從 [DiscretizationMethod] 旁邊的下拉式清單中，選取將成員分組的方法。 如需 **DiscretizationMethod** 設定的詳細資訊，請參閱 [Group Attribute Members &#40;Discretization&#41;](attribute-properties-group-attribute-members.md) (群組屬性成員 (分隔))。  
  
  