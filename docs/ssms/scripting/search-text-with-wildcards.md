---
title: 使用萬用字元搜尋文字
description: 了解如何在 [尋找和取代] 對話方塊的 [尋找目標] 欄位使用萬用字元，以指定相符的模式。
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.technology: ssms
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- vswildcardsbuilder
helpviewer_keywords:
- searches [SQL Server Management Studio], wildcards
- Query Editor [SQL Server Management Studio], wildcard searches
- wildcard options [SQL Server Management Studio]
ms.assetid: 449600f8-cc87-4b3f-878a-59c158a88a40
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f8f8ece77ca6d756ff621ded095e25e062508a23
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036338"
---
# <a name="search-text-with-wildcards"></a>使用萬用字元搜尋文字
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
  下列運算式可以取代 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [尋找和取代] 對話方塊中 [尋找目標] 欄位的字元或數字。  
  
#### <a name="to-search-using-wildcards"></a>若要利用萬用字元搜尋  
  
1.  若要在 [快速尋找]、 **[檔案中尋找]** 、 **[快速取代]** 或 **[檔案中取代]** 等作業期間，在 **[尋找目標]** 欄位中啟用萬用字元，請在 **[尋找選項]** 之下，選取 **[使用]** 選項，再選擇 **[萬用字元]**。  
  
2.  之後，就可以使用 **[尋找目標]** 欄位旁三角形的 **[參考清單]** 按鈕。 請按一下這個按鈕來顯示可用萬用字元的清單。 當您從 **[參考清單]** 中選擇任何項目時，項目會插入 **[尋找目標]** 字串中。  
  
 下表說明 **[參考清單]** 中可用的萬用字元。  
  
|運算是|語法|描述|  
|----------------|------------|-----------------|  
|任何單一字元|?|符合任何單一字元。|  
|任何單一位數|#|符合任何單一位數。 例如，7# 符合在 7 後面接著另一個數字的數字，如 71，17 便不符合。|  
|不在集合中的字元|[! ]|符合集合中所未指定的任何字元。|  
|一或多個字元|*|符何任何一或多個字元。 例如，new* 符合任何包括 "new" 的文字，如 newfile.txt。|  
|字元集|[ ]|符合集合中所指定的任何一個字元。|  
  
## <a name="see-also"></a>另請參閱  
 [搜尋和取代](./search-and-replace.md)   
 [使用規則運算式搜尋文字](./search-text-with-regular-expressions.md)