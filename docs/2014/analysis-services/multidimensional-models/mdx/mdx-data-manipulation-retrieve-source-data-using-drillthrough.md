---
title: 使用鑽取來抓取來源資料（MDX） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DRILLTHROUGH statement
- retrieving data
- queries [MDX], DRILLTHROUGH statement
- data retrieval [MDX]
ms.assetid: fe0ab170-25a9-45a8-a377-f71a67f77018
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b437016cc29b2e4a85f781e3a422fb40c70f37c3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "66074294"
---
# <a name="using-drillthrough-to-retrieve-source-data-mdx"></a>使用 DRILLTHROUGH 擷取來源資料 (MDX)
  多維度運算式 (MDX) 使用 [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough)陳述式從來源資料擷取 Cube 資料格的資料列集。  
  
 必須定義 Cube 的鑽研動作，才能在該 Cube 上執行 `DRILLTHROUGH` 陳述式。 若要定義鑽研動作，請在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 的 Cube 設計師中，於 [動作]**** 窗格的工具列上，按一下 [新增鑽研動作]****。 在新增的鑽研動作中，指定動作名稱、目標、條件，以及 `DRILLTHROUGH` 陳述式所傳回的資料行。  
  
## <a name="drillthrough-statement-syntax"></a>DRILLTHROUGH 陳述式語法  
 
  `DRILLTHROUGH` 陳述式使用以下語法：  
  
```  
<drillthrough> ::= DRILLTHROUGH [<Max_Rows>] [<First_Rowset>] <MDX select> [<Return_Columns>]  
   < Max_Rows> ::= MAXROWS <positive number>  
   <First_Rowset> ::= FIRSTROWSET <positive number>  
   <Return_Columns> ::= RETURN <member or attribute> [, <member or attribute>]  
```  
  
 
  `SELECT` 子句可識別包含所要擷取之來源資料的 Cube 資料格。 除了在 `SELECT` 子句中每個座標軸只能指定一個成員之外，此 `SELECT` 子句跟一般的 MDX `SELECT` 陳述式相同。 如果在一個座標軸上指定多個成員，就會發生錯誤。  
  
 
  `<Max_Rows>` 語法可指定每個傳回之資料列集中的最大資料列數目。 如果用以連接資料來源的 OLE DB 提供者不支援 `DBPROP_MAXROWS`，就會忽略 `<Max_Rows>` 設定。  
  
 
  `<First_Rowset>` 語法可識別最早將資料列集傳回的資料分割。  
  
 
  `<Return_Columns>` 語法可識別要傳回的基礎資料庫資料行。  
  
## <a name="drillthrough-statement-example"></a>DRILLTHROUGH 陳述式範例  
 以下範例示範 `DRILLTHROUGH` 陳述式的用法。 在此範例中，DRILLTHROUGH 陳述式會沿著 Stores 維度 (Slicer 軸)，查詢 Store、Product 及 Time 維度的分葉，然後傳回部門量值群組、部門識別碼及員工的姓氏。  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## <a name="see-also"></a>另請參閱  
 [&#40;MDX&#41;運算元據](mdx-data-manipulation-manipulating-data.md)  
  
  
