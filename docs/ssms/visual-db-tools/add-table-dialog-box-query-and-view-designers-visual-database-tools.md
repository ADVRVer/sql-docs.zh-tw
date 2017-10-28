---
title: "加入資料表對話方塊 (查詢和檢視表設計工具) (Visual DB Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdt.dlgbox.query.addtable
- vdtsql.chm:65565
ms.assetid: fce7adcc-4cf5-4a52-9203-11c13d1ecf08
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f65c7dfb218052015e9cbc818b2829faca5cf4ae
ms.contentlocale: zh-tw
ms.lasthandoff: 08/18/2017

---
# <a name="add-table-dialog-box-query-and-view-designers-visual-database-tools"></a>加入資料表對話方塊 (查詢和檢視表設計工具) (Visual Database Tools)
這個對話方塊可讓您將資料表、檢視、使用者自訂函數或同義字加入查詢或檢視中。  
  
> [!NOTE]  
> 如果資料表是要發佈以進行複寫，則必須使用 Transact-SQL 陳述式 [ALTER TABLE](http://msdn.microsoft.com/en-us/f1745145-182d-4301-a334-18f799d361d1) 或 SQL Server 管理物件 (SMO) 變更結構描述。 使用 [資料表設計工具] 或 [資料庫圖表設計工具] 變更結構描述時，會嘗試卸除並重新建立資料表。 您無法卸除已發行的物件，因此結構描述變更將會失敗。  
  
## <a name="options"></a>選項。  
**資料表**  
列出可以新增至 [圖表] 窗格的資料表。 若要新增資料表，請選取資料表，再按 [新增]。 若要一次新增數個資料表，請選取資料表，再按 [新增]。  
  
**檢視**  
列出可以新增至 [圖表] 窗格的檢視表。 若要新增檢視表，請選取檢視表，再按 [新增]。 若要一次新增數個檢視表，請選取檢視表，再按 [新增]。  
  
**函數**  
列出可新增至 [圖表] 窗格的使用者定義函數。 若要新增函數，請選取函數，再按 [新增]。 若要一次新增數個函數，請選取函數，再按 [新增]。  
  
**同義字**  
列出可新增至 [圖表] 窗格的同義資料表。 若要新增同義資料表，請選取同義資料表，再按 [新增]。 若要一次新增數個同義資料表，請選取同義資料表，再按一下 [新增]。  
  
**重新整理**  
更新清單以包含自上次擷取清單以來對資料庫所做的任何變更。  
  
**加入**  
加入選取的一或多個項目。  
  
## <a name="see-also"></a>另請參閱  
[設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  

