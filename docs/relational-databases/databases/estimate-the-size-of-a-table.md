---
title: "估計資料表的大小 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pages [SQL Server], space
- space [SQL Server], tables
- row size [SQL Server]
- size [SQL Server], tables
- column size [SQL Server]
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- disk space [SQL Server], tables
- space allocation [SQL Server], table size
- designing databases [SQL Server], estimating size
- reserved free rows per page [SQL Server]
- calculating table size
ms.assetid: 15c17c92-616f-402e-894b-907a296efe5f
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 740800db335b524298c39a3ab9f225e18d785c54
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="estimate-the-size-of-a-table"></a>估計資料表的大小
  您可以使用下列步驟來估計將資料儲存於資料表中所需的空間量：  
  
1.  遵循 [估計堆積的大小](../../relational-databases/databases/estimate-the-size-of-a-heap.md) 或 [估計叢集索引的大小](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)中的指示，來計算堆積或叢集索引所需的空間。  
  
2.  對於每個非叢集索引，請遵循 [估計非叢集索引的大小](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)中的指示，來計算其所需的空間。  
  
3.  新增步驟 1 和 2 中計算的值。  
  
## <a name="see-also"></a>另請參閱  
 [估計資料庫的大小](../../relational-databases/databases/estimate-the-size-of-a-database.md)   
 [估計堆積的大小](../../relational-databases/databases/estimate-the-size-of-a-heap.md)   
 [估計叢集索引的大小](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)   
 [估計非叢集索引的大小](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)  
  
  
