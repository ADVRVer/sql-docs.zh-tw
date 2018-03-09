---
title: "動態資料指標 |Microsoft 文件"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursors [ADO], dynamic
- dynamic cursors [ADO]
ms.assetid: 00460f30-8cf7-494e-82df-41012f40ae51
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dbeb8f40cf6d1ad91a59fa9719410f26386953d4
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="dynamic-cursors"></a>動態資料指標
動態資料指標偵測結果集中資料列，不論是否發生的變更從資料指標內或資料指標之外的其他使用者所做的變更。 所有的 insert、 update 和 delete 陳述式所做的所有使用者可透過資料指標。 動態資料指標可以偵測資料列、 順序和結果集資料指標開啟後的值所做的變更。 （除非資料指標交易隔離等級設定為 「 未認可 」），認可之前，不會顯示資料指標之外所做的更新。  
  
 例如，假設動態資料指標會擷取兩個資料列和另一個應用程式，然後更新那些資料列的其中一個並刪除其他。 如果動態資料指標，然後擷取這些資料列，將不會發現已刪除的資料列，但它會顯示更新的資料列的新值。  
  
 如果您的應用程式必須偵測到所有其他使用者所進行的並行更新，動態資料指標會是不錯的選擇。 使用**adOpenDynamic CursorTypeEnum**來指出您想要使用動態資料指標在 ADO 中。  
  
## <a name="see-also"></a>另請參閱  
 [順向資料指標](../../../ado/guide/data/forward-only-cursors.md)   
 [靜態資料指標](../../../ado/guide/data/static-cursors.md)   
 [索引鍵集資料指標](../../../ado/guide/data/keyset-cursors.md)
