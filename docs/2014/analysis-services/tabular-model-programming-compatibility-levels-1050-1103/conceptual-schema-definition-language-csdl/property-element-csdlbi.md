---
title: Property 元素 (CSDLBI) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: f0770c5e-6420-4d0c-a5bf-b94eaf6877ca
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 48442ba8e5d17a652f60aaebb24040345bda474f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055388"
---
# <a name="property-element-csdlbi"></a>Property 元素 (CSDLBI)
  CSDLBI 中的 Property 元素是複雜類型，它為 CSDL Property 元素提供了新增功能，以支援商業智慧資料模型。  
  
## <a name="elements-and-attributes"></a>元素和屬性  
 下表列出定義 CSDLBI Property 元素的元素和屬性。  
  
|名稱|是否必要|描述|  
|----------|-----------------|-----------------|  
|目錄|否|包含要求 LCID 的字串。|  
|DefaultAggregationFunction|是|字串，指定對屬性執行計算且未指定其他函數時，應使用的彙總函式。<br /><br /> 如果未指定，則會使用模型的預設彙總，通常是 SUM。|  
|GroupingBehavior|否|值，指定查詢結果分組的方式。 屬性的內容是由 TGroupingBehavior 簡單類型定義 (請參閱下表)。|  
|OrderBy|否|模型內另一個屬性的參考，該屬性會定義該屬性之值的排序次序。<br /><br /> 兩個屬性的值「應該」具有一對一對應。 否則，排序行為會是未定義。<br /><br /> 如果省略此元素，屬性會依據其值排序。|  
|Stability|否|指定重新整理作業之間屬性 (Property) 值穩定性的屬性 (Attribute)。<br /><br /> 此屬性不是由使用者設定，而是設計階段環境僅針對不穩定的值所發出。 此屬性一律套用至包含資料列號碼的資料行，以及包含產生未定結果 (例如 NOW() 或 RAND()) 之公式的資料行。<br /><br /> 下表列出此屬性的值，其描述 Stabilitysimple 類型。|  
  
## <a name="groupingbehavior"></a>GroupingBehavior  
 下表列出 GroupingBehavior 簡單類型的值。  
  
|值|描述|  
|-----------|-----------------|  
|GroupOnValue|依 xthe 屬性的值分組。|  
|GroupOnEntityKey|依實體索引鍵分組。|  
  
 下列範例說明這兩個值的用法。 假設查詢設計為傳回依名稱指定之特定使用者的薪資發放推算。 假設資料庫包含兩個同名但資料庫識別碼不同的使用者，則查詢結果會依據套用至資料行的屬性值而有所不同：  
  
-   `GroupOnValue`：查詢結果包含這兩位使用者的薪資發放推算，並且會將兩者加總。  
  
-   `GroupOnEntityKey`：查詢結果包含每一位使用者的薪資發放推算，並且分別列出。  
  
## <a name="stability"></a>Stability  
 下表列出 `Stability` 簡單類型的值。  
  
|值|描述|  
|-----------|-----------------|  
|Stable|屬性在重新整理作業之間會維持不變。|  
|RowNumber|屬性包含資料列號碼。|  
|Volatile|屬性在重新整理作業之間可能不會維持不變。|  
  
## <a name="example"></a>範例  
 **表格式**  
  
 下列 XML 顯示 CSDLBI 1.1 版中 AdventureWorks 表格式模型範本中某些屬性的表示法。  
  
```  
  
<EntityType   
   Name="DimEmployee">  
   <Key>  
      <PropertyRef   
      Name="RowNumber" />  
   </Key>  
  
   <Property   
      Name="RowNumber"   
      Type="Int64"   
      Nullable="false">  
   <bi:Property   
      Hidden="true"   
      Contents="RowNumber"   
      Stability="RowNumber" />  
   </Property>  
  
   <Property   
      Name="EmployeeKey"   
      Type="Int64">  
   <bi:Property />  
   </Property>  
….  
</bi:EntityType>  
</EntityType>  
  
```  
  
## <a name="example"></a>範例  
 **多維度**  
  
 下列 CSDLBI 1.1 版中的範例顯示資料模型中，代表 Contoso Operations Cube 的某些資料行屬性。 請注意，BI 註解並非必要，也不會套用至大部分資料行，只會套用至展示層中需要特別處理的資料行。  
  
```  
  
<EntityType   
   Name="Bike">  
  
   <Key>  
      <PropertyRef Name="RowNumber" />  
   </Key>  
  
   <Property   
      Name="RowNumber"   
      Type="Int64"   
      Nullable="false">  
   <bi:Property   
      Hidden="true"   
      Contents="RowNumber"   
      Stability="RowNumber"   
   />  
   </Property>  
  
   <Property   
      Name="ProductAlternateKey"   
      Type="String"   
      MaxLength="Max"   
      Unicode="true"   
      FixedLength="false">  
   <bi:Property />  
   </Property>  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [CSDL 之 BI 註解的技術參考](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
