---
description: '&lt;來源資料查詢 &gt; -圖形'
title: " (DMX) 的形狀 |Microsoft Docs"
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 16fff086514facbb8197d8d6f27b72b81f67c2e2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500771"
---
# <a name="ltsource-data-querygt---shape"></a>&lt;來源資料查詢 &gt; -圖形
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  將多個資料來源的查詢結合到單一階層式資料表 (亦即，有巢狀資料表的資料表)，這個資料表會成為採礦模型的案例資料表。  
  
 **SHAPE**命令的完整語法記載于 [!INCLUDE[msCoName](../includes/msconame-md.md)] Data ACCESS Components (MDAC) 軟體發展工具組 (SDK) 。  
  
## <a name="syntax"></a>語法  
  
```  
  
SHAPE {<primary query>}  
APPEND ({ <child table query> }   
     RELATE <primary column> TO <child column>)   
          AS <column table name>  
[  
     ({ <child table query> }   
     RELATE <primary column> TO <child column>)   
          AS < column table name>  
...  
]       
```  
  
## <a name="arguments"></a>引數  
 *主要查詢*  
 傳回父資料表的查詢。  
  
 *子資料工作表查詢*  
 傳回巢狀資料表的查詢。  
  
 *主要資料行*  
 父資料表中，識別子資料表查詢結果中之子資料列的資料行。  
  
 *子資料行*  
 子資料工作表中的資料行，用來識別主要查詢結果中的父資料列。  
  
 *資料行資料表名稱*  
 巢狀資料表中，父資料表內新附加的資料行名稱。  
  
## <a name="remarks"></a>備註  
 您必須根據會建立父資料表與子資料表之關聯性的資料行來排序查詢。  
  
## <a name="examples"></a>範例  
 您可以在 [INSERT INTO &#40;DMX&#41;](../dmx/insert-into-dmx.md) 語句內使用下列範例，將包含嵌套資料表的模型定型。 **SHAPE**語句內的兩個數據表是透過**OrderNumber**資料行來相關的。  
  
```  
SHAPE {  
    OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
```  
  
## <a name="see-also"></a>另請參閱  
 [&#60;來源資料查詢&#62;](../dmx/source-data-query.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 資料定義語句](../dmx/dmx-statements-data-definition.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 資料動作陳述式](../dmx/dmx-statements-data-manipulation.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 陳述式參考](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
