---
title: 在圖表上建立資料表之間的關聯性
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- diagrams [SQL Server], designing
ms.assetid: 28e9630c-dff4-46cc-bb0e-fe77998b6ac2
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: eb0d82c1693c452462b8bef2e55cd4e41b13689b
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "79198383"
---
# <a name="create-relationships-between-tables-on-a-diagram-visual-database-tools"></a>在圖表上建立資料表之間的關聯性 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
在圖表設計工具中，您可以在資料表之間拖曳資料行，以建立不同資料表資料行之間的關聯性。  
  
### <a name="to-create-a-relationship-graphically"></a>若要以圖形建立關聯性  
  
1.  在資料庫設計工具中，針對一個或多個要關聯到其他資料表資料行的資料庫資料行，按一下資料列選取器。  
  
2.  將選取的資料行拖曳到關聯的資料表。  
  
3.  會出現兩個對話方塊：[外部索引鍵關聯性]  和 [資料表與資料行]  ，而後者會顯示在前景中。  
  
4.  [關聯性名稱]  具有系統提供的名稱，其格式為 FK_*localtable*\_*foreigntable*。 您可以變更這個值。  
  
5.  確認 [主索引鍵資料表]  是否指定正確的資料表。  
  
6.  方格會列出本地資料行及其對應的外部資料行。 您可以加入或移除資料表資料行，或變更對應。  
  
7.  選擇 [確定]  。  
  
    [外部索引鍵關聯性]  對話方塊便會出現。 [選取的關聯性]  會顯示您所建立的關聯性。  
  
8.  變更方格中關聯性的屬性。  
  
9. 選擇 **[確定]** 建立關聯性。  
  
    資料庫設計工具會顯示您選擇的資料行之間的關聯性。  
  
## <a name="see-also"></a>另請參閱  
[資料表和資料行對話方塊 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/tables-and-columns-dialog-box-visual-database-tools.md)  
[使用條件約束](https://msdn.microsoft.com/637098af-2567-48f8-90f4-b41df059833e)  
[使用資料庫圖表中的資料表 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/work-with-tables-in-database-diagram-visual-database-tools.md)  
  
