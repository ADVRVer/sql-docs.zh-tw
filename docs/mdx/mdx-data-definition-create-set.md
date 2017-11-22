---
title: "CREATE SET 陳述式 (MDX) |Microsoft 文件"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET
- CREATE SET
- CREATE_SET
- CREATE
dev_langs: kbMDX
helpviewer_keywords:
- named sets [MDX]
- CREATE SET statement
ms.assetid: eff51eeb-5e7e-4706-b861-c57b6f3f89f0
caps.latest.revision: "42"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6684e5b5d8edd630e623e5210d977c70903b01c5
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="mdx-data-definition---create-set"></a>MDX 資料定義-建立設定
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  使用目前 Cube 的工作階段範圍來建立命名集。  
  
## <a name="syntax"></a>語法  
  
```  
  
CREATE [SESSION] [ STATIC | DYNAMIC ] [HIDDEN] SET   
   CURRENTCUBE | Cube_Name  
      .Set_Name AS 'Set_Expression'  
      [,Property_Name = Property_Value, ...n]  
```  
  
## <a name="arguments"></a>引數  
 *Cube_Name*  
 提供 Cube 名稱的有效字串運算式。  
  
 *Set_Name*  
 提供所建立之命名集名稱的有效字串運算式。  
  
 *Set_Expression*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *Property_Name*  
 提供集合屬性名稱的有效字串。  
  
 *Property_Value*  
 定義集合屬性值的有效純量運算式。  
  
## <a name="remarks"></a>備註  
 命名集是建立以供再次使用的維度成員集合 (或定義集合的運算式)。 例如，命名集可以定義一個維度成員集合，此集合是由依銷售業績排名的前十名商店所組成。 以靜態方式，或透過類似的函式，這一組可以定義[TopCount](../mdx/topcount-mdx.md)。 然後就可以在需要前十名商店的集合之時，使用此命名集。  
  
 CREATE SET 陳述式建立的命名集可在整個工作階段中使用，因此，此命名集可用於工作階段中的多個查詢。 如需詳細資訊，請參閱[Creating Session-Scoped 導出成員 &#40;MDX &#41;](../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md).  
  
 您也可以定義供單一查詢使用的命名集。 若要定義這類集合，您可以在 SELECT 陳述式中使用 WITH 子句。 如需 WITH 子句的詳細資訊，請參閱[Creating Query-Scoped 命名集 &#40;MDX &#41;](../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md).  
  
 *如此*子句可以包含任何支援 MDX 語法的函式。 使用未指定 SESSION 子句的 CREATE SET 陳述式而建立的集合會有工作階段範圍。 使用 WITH 子句來建立含查詢範圍的集合。  
  
 指定目前連接之 Cube 以外的 Cube 會導致發生錯誤。 因此，您應該使用 CURRENTCUBE 取代 Cube 名稱，來代表目前的 Cube。  
  
## <a name="scope"></a>範圍。  
 使用者自訂集合可發生在下表列出的其中一個範圍內。  
  
 查詢範圍  
 集合的可見性與存留時間受限於查詢。 集合是在個別查詢中定義。 查詢範圍可覆寫工作階段範圍。 如需詳細資訊，請參閱[Creating Query-Scoped 命名集 &#40;MDX &#41;](../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md).  
  
 工作階段範圍  
 集合的可見性與存留時間受限於其建立所在的工作階段。 (如果 DROP SET 陳述式是在集合上發出，存留時間就會比工作階段期間短)。CREATE SET 陳述式會以工作階段範圍建立集合。 使用 WITH 子句來建立含查詢範圍的集合。  
  
### <a name="example"></a>範例  
 下列範例會建立名稱 Core Products 的集合。 然後 SELECT 查詢示範呼叫新建的集合。 CREATE SET 陳述式必須先執行，然後才能執行 SELECT 查詢 - 它們不能在相同批次中同時執行。  
  
```  
CREATE SET [Adventure Works].[Core Products] AS '{[Product].[Category].[Bikes]}'  
  
SELECT [Core Products] ON 0  
  FROM [Adventure Works]  
```  
  
## <a name="set-evaluation"></a>集合評估  
 組合評估可以定義為以不同方式發生，例如，可以定義為僅在建立集合時發生一次，或定義為每次使用集合時都發生。  
  
 STATIC  
 表示僅在評估 CREATE SET 陳述式時，評估集合一次。  
  
 DYNAMIC  
 表示每次在查詢中使用時，都評估集合。  
  
## <a name="set-visibility"></a>設定可視性  
 查詢 Cube 的其他使用者看得到或看不到集合。  
  
 HIDDEN  
 指定查詢 Cube 的使用者看不到集合。  
  
## <a name="standard-properties"></a>標準屬性  
 每個集合都有一組預設屬性。 當用戶端應用程式連接至[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的預設屬性是直接或可以受到支援，由系統管理員決定。  
  
|屬性識別碼|意義|  
|-------------------------|-------------|  
|CAPTION|用戶端應用程式當做集合標題使用的字串。|  
|DISPLAY_FOLDER|識別用戶端應用程式用於顯示集合之顯示資料夾路徑的字串。 資料夾層級的分隔符號是由用戶端應用程式所定義。 工具和用戶端所提供的[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]，反斜線 (\\) 為層級分隔符號。 若要針對已定義的集合提供多個顯示資料夾，請使用分號 (;) 來分隔資料夾。|  
  
## <a name="see-also"></a>請參閱＜  
 [DROP SET 陳述式 &#40;MDX &#41;](../mdx/mdx-data-definition-drop-set.md)   
 [MDX 資料定義陳述式 &#40;MDX &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
