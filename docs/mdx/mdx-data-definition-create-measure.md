---
description: MDX 資料定義 - CREATE MEASURE
title: CREATE MEASURE 語句 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cdbee6f6ede5e46926f1a8189792d86cf9e99f5b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387264"
---
# <a name="mdx-data-definition---create-measure"></a>MDX 資料定義 - CREATE MEASURE


  在表格式模型中建立量值。  
  
## <a name="syntax"></a>語法  
  
```  
  
CREATE MEASURE Table_Name[Measure_Name] = DAX_Expression  
[; CREATE MEASURE ...n]  
  
```  
  
## <a name="arguments"></a>引數  
 *Table_Name*  
 提供將建立量值之資料表名稱的有效字串常值。  
  
 *Measure_Name*  
 提供量值名稱的有效字串常值。  
  
 *DAX_Expression*  
 傳回單一純量值的有效 DAX 運算式。  
  
## <a name="remarks"></a>備註  
 *Measure_Name*必須以括弧括住。  
  
 CREATE MEASURE 語句只能在 MDX 腳本定義內部使用;請參閱 [MdxScript 元素 &#40;ASSL&#41;](https://docs.microsoft.com/analysis-services/assl/objects/mdxscript-element-assl?view=asallproducts-allversions)。  
  
 您也可以定義供單一查詢使用的導出成員。 若要定義受限於單一查詢的導出成員，您可以在 SELECT 陳述式中使用 WITH 子句。 如需詳細資訊，請參閱 [在 MDX 中建立量值](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-building-measures)。  
  
## <a name="see-also"></a>另請參閱  
 [Mdx 資料定義語句 &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
