---
title: MSSQLSERVER_9532 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9532 (Database Engine error)
ms.assetid: ab95cce8-4f97-4aea-a746-a73eea7c9aab
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f811d554ea59539bd558e1c22c19fb118e54820f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "62912405"
---
# <a name="mssqlserver_9532"></a>MSSQLSERVER_9532
    
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|9532|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|XMLERR_COLUMNSET_CANNOT_CONVERT_FROM_TO|  
|訊息文字|在包含資料行集 '%.*ls' 的查詢/DML 作業中，將資料行 '%.\*ls' 從資料類型 '%ls' 轉換成資料類型 '%ls' 時，轉換失敗。|  
  
## <a name="explanation"></a>說明  
 資料行集是不具類型的 XML 表示，可將資料表的某些資料行結合到結構化輸出中。 當您透過 XML 資料行集來插入或更新疏鬆資料行值時，插入基礎疏鬆資料行內的值會從 `xml` 資料類型隱含地轉換。 提供了無法轉換成此資料行之資料類型的值。  
  
## <a name="user-action"></a>使用者動作  
 由於提供的值無法隱含地轉換，所以它可能是無效的輸入。 請更正錯誤後重試。 如果此值正確無誤，請修改陳述式來使用個別資料行，而非資料行集。 如此可讓您明確地將此值轉換成正確的資料類型。  
  
  
