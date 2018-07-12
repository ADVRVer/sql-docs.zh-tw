---
title: Level 元素 (CSDLBI) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fdf75c47-77dc-4bdb-9931-8eca198fdb88
caps.latest.revision: 10
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3fd89aaa69e8dc2b29b80ca82f89d1453dc44017
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211478"
---
# <a name="level-element-csdlbi"></a>Level 元素 (CSDLBI)
  Level 元素是複雜類型，會定義階層中的單一層級。  
  
## <a name="elements-and-attributes"></a>元素和屬性  
 下表列出定義 Level 元素的元素和屬性。  
  
|名稱|是否必要|描述|  
|----------|-----------------|-----------------|  
|來源|是|屬性參考的容器。|  
|PropertyRef|是|執行個體屬性的參考。 層級的其他屬性 (例如標題、名稱及參考名稱) 都可以從參考的執行個體屬性中取得。 這樣您就不需要在 Level 元素中指定這些屬性。|  
  
## <a name="remarks"></a>備註  
 如需表格式模型中階層的詳細資訊，請參閱 [Hierarchy 元素 &#40;CSDLBI&#41;](hierarchy-element-csdlbi.md)。  
  
## <a name="example"></a>範例  
 **表格式**  
  
 下列 CSDLBI 1.1 版中的範例會根據 AdventureWorks 表格式模型範例顯示階層中多個層級的定義。  
  
```  
  
<bi:Hierarchy Name="Category">  
   <bi:Level Name="CategoryName">  
     <bi:Source>  
       <bi:PropertyRef Name="CategoryName" />  
     </bi:Source>  
   </bi:Level>  
   <bi:Level Name="ProductName">  
     <bi:Source>  
       <bi:PropertyRef Name="ProductName" />  
     </bi:Source>  
   </bi:Level>  
</bi:Hierarchy>  
```  
  
## <a name="example"></a>範例  
 **多維度**  
  
 下列 CSDLBI 1.1 版中的範例會顯示來自 Contoso Operations Cube 且具有多個層級的階層。  
  
```  
<bi:Hierarchy   
   Name="Product_Hierarchy"   
   Caption="Product Hierarchy"   
   ReferenceName="Product Hierarchy">  
     <bi:Documentation>  
        <bi:Summary>DESCRIPTION_ProductModelCateg_Hierarchies</bi:Summary>  
     </bi:Documentation>  
  
     <bi:Level Name="ProductLine">  
        <bi:Source>  
        <bi:PropertyRef Name="ProductLine" />  
        </bi:Source>  
     </bi:Level>  
  
     <bi:Level Name="ModelName">  
        <bi:Source>  
        <bi:PropertyRef Name="ModelName" />  
        </bi:Source>  
     </bi:Level>  
</bi:Hierarchy>  
```  
  
## <a name="see-also"></a>另請參閱  
 [了解表格式物件模型](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [了解 DAX 中父子式階層的函數](https://msdn.microsoft.com/library/gg492192(v=sql.120).aspx)   
 [設定&#40;所有&#41;屬性階層的層級](../../multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
