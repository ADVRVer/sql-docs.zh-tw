---
title: "UPDATE 陳述式的限制 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 502315916781ae5624f94e099c0cd95c52ffe8a8
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2017
---
# <a name="update-statement-limitations"></a>UPDATE 陳述式的限制
Paradox 驅動程式來更新資料表時，該資料表必須有唯一的索引 （Paradox 主索引鍵）。 當您使用 Paradox 驅動程式而不需要實作 Borland Database Engine 時，它不更新 Paradox 資料表。  
  
 不支援文字驅動程式。  
  
 使用 Microsoft Excel 驅動程式時，便可更新的值，但無法從 Microsoft Excel 試算表為基礎的資料表中刪除資料列。 如此一來，UPDATE 陳述式不是正式支援 Microsoft Excel 驅動程式。 INSERT 陳述式會視為受支援。
