---
title: 鑽取語句（MDX） |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ee90d2c367fa289e8255a84e4eb6da19b37933e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68891208"
---
# <a name="mdx-data-manipulation---drillthrough"></a>MDX 資料操作 - DRILLTHROUGH


  擷取在 Cube 中用來建立指定資料格的基礎資料表資料列。  
  
## <a name="syntax"></a>語法  
  
```  
  
DRILLTHROUGH[MAXROWSUnsigned_Integer]   
      <MDX SELECT statement>   
      [RETURNSet_of_Attributes_and_Measures   
            [,Set_of_Attributes_and_Measures ...]  
      ]  
```  
  
## <a name="arguments"></a>引數  
 *Unsigned_Integer*  
 正整數值。  
  
 *MDX SELECT 語句*  
 任何有效的多維度運算式 (MDX) 運算式 SELECT 陳述式。  
  
 *Set_of_Attributes_and_Measures*  
 以逗號分隔的維度屬性和量值清單。  
  
## <a name="remarks"></a>備註  
 在鑽研作業中，使用者會從 Cube 選取單一資料格，並且從該資料格的來源資料中擷取結果集，以便取得更詳細的資訊。 依預設，鑽研結果集是從評估以計算所選 Cube 資料格之值的資料表資料列衍生而來。 若要讓使用者能執行鑽研，用戶端應用程式必須支援此功能。 在[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]中，除非查詢 ROLAP 資料分割或維度，否則會直接從 MOLAP 儲存體中取出結果。  
  
> [!IMPORTANT]  
>  鑽研安全性是以定義於 Cube 的一般安全性選項為基礎。 如果使用者無法透過 MDX 取得某些資料，鑽研也會以完全相同的方式限制使用者。  
  
 MDX 陳述式可指定主旨資料格。 **MAXROWS**引數所指定的值會指出產生的資料列集應傳回的最大資料列數目。  
  
 根據預設，傳回的資料列數上限為 10,000 個資料列。 這表示，如果您將**MAXROWS**保留為未指定，則會得到10000個或更少的資料列。 如果您的案例的此值太低，您可以將**MAXROWS**設定為較高的數位， `MAXROWS 20000`例如。 如果整體不足，您可以藉由變更**OLAP\Query\DefaultDrillthroughMaxRows**伺服器屬性來增加預設值。 如需變更此屬性的詳細資訊，請參閱[Analysis Services 中的伺服器屬性](https://docs.microsoft.com/analysis-services/server-properties/server-properties-in-analysis-services)。  
  
 除非另有指定，否則所傳回的資料行會包含與指定量值之量值群組相關的所有維度 (多對多維度除外) 之全部資料粒度屬性。 Cube 維度前面有 $，以區分維度和量值群組。 **RETURN**子句是用來指定由「鑽取」查詢所傳回的資料行。 下列函數可以套用至單一屬性，或由**RETURN**子句來測量。  
  
 Name(attribute_name)  
 傳回指定屬性成員的名稱。  
  
 UniqueName(attribute_name)  
 傳回指定屬性成員的唯一名稱。  
  
 Key(attribute_name[, N])  
 傳回指定屬性成員的索引鍵，其中 N 指定複合索引鍵 (如果有的話) 的資料行。 N 的預設值是 1。  
  
 Caption(attribute_name)  
 傳回指定之屬性成員的標題。  
  
 MemberValue(attribute_name)  
 傳回指定之屬性成員的成員值。  
  
 CustomRollup(attribute_name)  
 傳回所指定屬性成員的自訂積存運算式。  
  
 CustomRollupProperties(attribute_name)  
 傳回所指定屬性 (Attribute) 成員的自訂積存屬性 (Property)。  
  
 UnaryOperator(attribute_name)  
 傳回所指定屬性成員的一元運算子。  
  
## <a name="example"></a>範例  
 下列範例會指定 2007 年 7 月澳大利亞轉售商銷售數量量值 (預設量值) 的資料格。 RETURN 子句會指定所傳回之資料格的基礎：每個銷售日期、產品型號名稱、員工名稱、銷售額、稅額及產品成本值。  
  
```  
DRILLTHROUGH  
SELECT  
   ([Date].[Calendar].[Month].[July 2007])  
ON 0   
FROM [Adventure Works]  
WHERE [Geography].[Country].[Australia]  
RETURN   
  [$Date].[Date]  
  ,KEY([$Product].[Model Name])  
  ,NAME([$Employee].[Employee])  
  ,[Reseller Sales].[Reseller Sales Amount]  
  ,[Reseller Sales].[Reseller Tax Amount]  
  ,[Reseller Sales].[Reseller Standard Product Cost]  
```  
  
## <a name="see-also"></a>另請參閱  
 [Mdx&#41;&#40;mdx 資料動作陳述式](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
