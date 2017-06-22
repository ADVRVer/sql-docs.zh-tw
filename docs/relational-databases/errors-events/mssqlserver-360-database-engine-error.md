---
title: MSSQLSERVER_360 | Microsoft Docs
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
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d4523266142da60eb89136be6209a5944cecbd5a
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver360"></a>MSSQLSERVER_360
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|360|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|DML_UPDATE_SPARSE_AND_COLSET|  
|訊息文字|INSERT、UPDATE 或 MERGE 陳述式的目標資料行清單中不可以同時包含疏鬆資料行和內含疏鬆資料行的資料行集。 請重寫陳述式，以包含疏鬆資料行或資料行集，而非同時包含兩者。|  
  
## <a name="explanation"></a>說明  
資料行集是不具類型的 XML 表示，可將資料表的某些資料行結合到結構化輸出中。 嘗試修改此資料行集以及此資料行集中所含的資料行，造成兩個項目參考相同的資料行。  
  
## <a name="user-action"></a>使用者動作  
請重寫陳述式，以包含對此資料行或資料行集的參考，但不要將這兩個參考同時包含在陳述式內。  
  

