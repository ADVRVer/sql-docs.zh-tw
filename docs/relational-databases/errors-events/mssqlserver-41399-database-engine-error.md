---
title: MSSQLSERVER_41399 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 41399 (Database Engine error)
ms.assetid: 5e5acb07-16ca-4329-8210-cd2bab0c904f
caps.latest.revision: 6
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f335d589b9dc5e1f500922a6bf2b63cacaf4bb90
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver41399"></a>MSSQLSERVER_41399
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|事件識別碼|41399|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|MAX_SORT_ROW_WIDTH_EXCEEDED|  
|訊息文字|排序作業太複雜。 請參閱《SQL Server 線上叢書》以取得詳細資訊。|  
  
## <a name="explanation"></a>說明  
將聯結和彙總作業的結果排序，會因為排序緩衝區中的資料列大小增加，而增加排序作業的複雜性。 此錯誤表示資料列的大小，超過原生編譯預存程序中排序運算子所支援的大小上限。 請注意，排序緩衝區中的資料列大小，僅取決於聯結數目及彙總函式的數目和類型。 基底資料表中的資料列大小，並不會影響緩衝區中的資料列大小。  
  
## <a name="user-action"></a>使用者動作  
移除聯結或彙總函式以減少查詢的複雜性。  
  
## <a name="see-also"></a>另請參閱  
[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

