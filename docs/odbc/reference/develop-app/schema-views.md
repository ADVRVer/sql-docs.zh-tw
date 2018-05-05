---
title: 結構描述檢視 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- schema views [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], schema views
ms.assetid: f1dfb3e8-a7bd-46c3-92b6-c19531e8409d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 686b13ff9b480a1e2e96a175fe546d064079d871
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="schema-views"></a>結構描述檢視
藉由呼叫 ODBC 目錄函數或藉由使用 INFORMATION_SCHEMA 檢視應用程式可以從 DBMS 擷取中繼資料資訊。 ANSI sql-92 標準所定義的檢視。  
  
 如果 DBMS 和驅動程式支援，INFORMATION_SCHEMA 檢視會提供擷取中繼資料，比 ODBC 目錄函數提供的功能更強大且完整方法。 應用程式可以執行它自己的自訂**選取**陳述式是否符合其中一個檢視，可以加入檢視，或可以在檢視上執行聯集。 同時提供更大的公用程式和廣泛的中繼資料，INFORMATION_SCHEMA 檢視不會經常受到 DBMS。 這可能會變更詳細的 Dbms 和驅動程式達到與 sql-92 的相容性。  
  
 若要判斷支援哪些檢視表，應用程式呼叫**SQLGetInfo** SQL_INFO_SCHEMA_VIEWS 選項。 若要從支援的檢視中擷取中繼資料，應用程式執行**選取**陳述式，指定所需的結構描述資訊。
