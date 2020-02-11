---
title: 維度（MDX） |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 84d5ab0caa22c6f35f3e7b790dbfb3348df8ceb1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67999972"
---
# <a name="dimensions-mdx"></a>Dimensions (MDX)


  傳回由數值或字串運算式所指定的階層。  
  
## <a name="syntax"></a>語法  
  
```  
  
Numeric expression syntax  
Dimensions(Hierarchy_Number)  
  
String expression syntax  
Dimensions(Hierarchy_Name)  
```  
  
## <a name="arguments"></a>引數  
 *Hierarchy_Number*  
 指定階層編號的有效數值運算式。  
  
 *Hierarchy_Name*  
 指定階層名稱的有效字串運算式。  
  
## <a name="remarks"></a>備註  
 如果指定了階層編號，**維度**函數會傳回階層，其在 cube 內以零為基底的位置是指定的階層編號。  
  
 如果指定了階層名稱， **dimension 函數會**傳回指定的階層。 一般來說，您會將此字串**版本的 dimension 函數與**使用者定義函數搭配使用。  
  
> [!NOTE]  
>  **量值**維度一律會以表示`Dimensions(0)`。  
  
## <a name="examples"></a>範例  
 下列範例會使用**維度**函數來傳回指定階層的名稱、層級計數和成員計數，同時使用數值運算式和字串運算式。  
  
```  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Levels.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Members.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Levels.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>另請參閱  
 [Mdx 函數參考 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
