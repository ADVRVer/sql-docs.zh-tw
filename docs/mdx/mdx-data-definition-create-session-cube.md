---
title: CREATE SESSION CUBE 語句（MDX） |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ac95afcebcf07a5d691db5f2599b3290b9587d44
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68038357"
---
# <a name="mdx-data-definition---create-session-cube"></a>MDX 資料定義 - CREATE SESSION CUBE


  根據現有的伺服器 Cube，建立並擴展工作階段 Cube。 工作階段 Cube 只有在目前工作階段中才可見，您無法從其他任何工作階段瀏覽或查詢。 關閉工作階段時就會隱含刪除工作階段 Cube。  
  
## <a name="syntax"></a>語法  
  
```  
  
CREATE SESSION CUBE session_cube_name FROM <cube list> (<param list>)  
  
<cube list>::= source_cube_name [,<cube list>]  
  
<param list>::= <param> ,<param list> | <param>  
  
<param>::= <dims list> | <measures list>  
  
<measures list>::= <measure>[, <measures list>]   
  
<dims list>::= <dim def> [, <dims list>]  
  
<measure>::= MEASURE source_cube_name.measure_name [<visibility qualifier>] [AS measure_name]   
  
<dim def>::= <source dim def> | <derived dim def>  
  
<source dim def>::= DIMENSION source_cube_name.dimension_name [<dim flags>] [<visibility qualifier>] [AS dimension_name>] [FROM <dim from clause> ] [<dim content def>]  
  
<dim flags>::= NOT_RELATED_TO_FACTS   
  
<dim from clause>::= <reg dim from clause>   
  
<dim reg from clause>::= dimension_name  
  
<dim content def>::= ( <level list> [,<grouping list>] [,<member slice list>] [,<default member>] )  
  
<level list>::= <level def> [, <level list>]  
  
<level def>::= LEVEL level_name [<level type> ] [AS level_name] [<level content def>]  
  
<level content def>::= ( <property list> ) | NO_PROPERTIES  
  
<level type>::= GROUPING  
  
<property list>::= <property def> [, <property list>]  
  
<property def>::= PROPERTY property_name   
  
<grouping list>::= <grouping entity> [,<grouping list>]  
  
<grouping entity>::= GROUP group_level_name.group_name (<mixed list>)  
  
<grp mixed list>::= <grp mixed element> [,<grp mixed list>]  
  
<grp mixed element>::= <grouping entity> | <member def>  
  
<member slice list>::= <member list>  
  
<member list>::= <member def> [, <member list>]  
  
<member def>::= MEMBER member_name  
  
<default member>::= DEFAULT_MEMBER AS MDX_expression  
  
<visibility qualifier>::= HIDDEN  
  
```  
  
## <a name="syntax-elements"></a>語法元素  
 session_cube_name  
 工作階段 Cube 的名稱。  
  
 source_cube_name  
 工作階段 Cube 所依據的 Cube 名稱。  
  
 source_cube_name.measure_name  
 包含在工作階段 Cube 內之來源量值的完整名稱。 不允許使用「量值」維度的導出成員。  
  
 measure_name  
 工作階段 Cube 中量值的名稱。  
  
 source_cube_name.dimension_name  
 包含在工作階段 Cube 內之來源維度的完整名稱。  
  
 dimension_name  
 工作階段 Cube 中維度的名稱。  
  
 FROM \<dim from 子句>  
 只適用於衍生維度定義的有效規格。  
  
 NOT_RELATED_TO_FACTS  
 只適用於衍生維度定義的有效規格。  
  
 \<層級類型>  
 只適用於衍生維度定義的有效規格。  
  
## <a name="remarks"></a>備註  
 工作階段 Cube 與伺服器和本機 Cube 不同，只要建立工作階段 Cube 的工作階段結束，該工作階段 Cube 就不復存在。 工作階段 Cube 是以定義它的量值和定義來定義。 維度有二種類型：  
  
-   來源維度 - 這些是屬於來源 Cube 的維度。  
  
-   衍生維度 - 這些是提供新分析功能的維度。 衍生維度可以是根據水平或垂直切割的來源維度所定義的一般維度，或包含自訂維度成員群組的一般維度。 衍生維度也可以是以資料採礦模型為基礎的資料採礦維度。  
  
> [!NOTE]  
>  Dimension 關鍵字所指的可以是維度或階層。  
  
 工作階段 Cube 主要用於將屬性成員組成動態群組，使屬性成員按照用戶端應用程式 (例如 Microsoft Excel) 分成自訂的成員群組。 在工作階段 Cube 中，您可以執行下列工作：  
  
-   刪除存在來源 Cube 中的維度。  
  
-   在維度中加入或刪除階層。  
  
-   刪除量值群組或特定量值。  
  
-   為了針對現有屬性建立群組，而根據屬性繫結加入新的屬性。  
  
> [!IMPORTANT]  
>  工作階段 Cube 物件的安全性係繼承自基礎來源物件。 工作階段 Cube 也會繼承其他物件，例如動作和計算指令碼。  
  
 CREATE SESSION CUBE 陳述式遵守下列規則：  
  
-   您無法對父子式階層執行組成群組。  
  
-   您無法對 ROLAP 維度執行組成群組。  
  
-   您無法對連結維度執行組成群組。  
  
-   您無法對具有自訂積存的層級執行組成群組。  
  
-   您無法對分隔式屬性階層執行組成群組。  
  
-   您無法對非自然階層執行組成群組，所謂非自然階層是指層級之間 (例如年齡和姓別之間) 存在多對多的關係。  
  
-   在 MDX 指令碼中明確參考 Cube 名稱，會因組成群組而變得不完整，因為工作階段 Cube 具有不同的名稱。 請改用 CURRENTCUBE 關鍵字。  
  
-   您無法對具有明確預設成員的維度執行組成群組。  
  
-   執行組成群組時，會卸除原始伺服器 Cube 的工作階段範圍導出成員。  
  
-   對伺服器 Cube 中的 Cube 維度執行組成群組時，該組成群組動作會影響以同一維度為基礎的所有 Cube 維度。  
  
## <a name="example"></a>範例  
 以下範例示範建立工作階段範圍版本的 Adventure Works Cube，其中包含 [轉售商銷售數量] 量值、[轉售商] 維度、[產品] 維度、[地理位置] 維度和 [日期] 維度。 在這個工作階段 Cube 中，會建立兩個群組，一個群組包含 Europe 的國家 (地區)，另一個群組包含 North America 的群組。 這個範例是當使用者建立自訂的成員群組時，由 Microsoft Excel 發出的 CREATE SESSION CUBE 陳述式的簡化版本。  
  
```  
CREATE SESSION CUBE [Adventure Works_XL_GROUPING1]   
   FROM [Adventure Works]   
   ( MEASURE [Adventure Works].[Internet Sales Amount]  
   ,MEASURE [Adventure Works].[Reseller Sales Amount]  
   ,DIMENSION [Adventure Works].[Date].[Calendar]  
   ,DIMENSION [Adventure Works].[Date].[Calendar Year]  
   ,DIMENSION [Adventure Works].[Date].[Calendar Semester]  
   ,DIMENSION [Adventure Works].[Date].[Calendar Quarter]  
   ,DIMENSION [Adventure Works].[Date].[Month Name]  
   ,DIMENSION [Adventure Works].[Date].[Date]  
   ,DIMENSION [Adventure Works].[Geography].[Country]   
      HIDDEN AS _XL_GROUPING81  
   ,DIMENSION [Adventure Works].[Geography].[State-Province]  
   ,DIMENSION [Adventure Works].[Geography].[City]  
   ,DIMENSION [Adventure Works].[Geography].[Postal Code]  
   ,DIMENSION [Adventure Works].[Geography].[Geography]  
   ,DIMENSION [Adventure Works].[Product].[Product Categories]  
   ,DIMENSION [Adventure Works].[Product].[Category]  
   ,DIMENSION [Adventure Works].[Product].[Subcategory]  
   ,DIMENSION [Adventure Works].[Product].[Product]  
   ,DIMENSION [Adventure Works].[Product].[Product Key]  
   ,DIMENSION [Adventure Works].[Reseller].[Reseller]  
   ,DIMENSION [Adventure Works].[Reseller].[Geography Key]  
   ,DIMENSION [Geography].[Country]   
      NOT_RELATED_TO_FACTS FROM _XL_GROUPING81   
          ( LEVEL [(All)]  
         ,LEVEL [Country1] GROUPING  
         ,LEVEL [Country]  
            ,GROUP [Country1].[CountryXl_Grp_1]   
                ( MEMBER [Geography].[Country].&[Canada]  
                  ,MEMBER [Geography].[Country].&[United States] )  
            ,GROUP [Country1].[CountryXl_Grp_2]   
                ( MEMBER [Geography].[Country].&[France]  
                  ,MEMBER [Geography].[Country].&[Germany]  
                  ,MEMBER [Geography].[Country].&[United Kingdom] )   
            )   
   )  
```  
  
## <a name="see-also"></a>另請參閱  
 [Mdx 資料定義語句 &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)   
 [CREATE GLOBAL CUBE 語句 &#40;MDX&#41;](../mdx/mdx-data-definition-create-global-cube.md)  
  
  
