---
title: MSSQLSERVER_9532 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 9532 (Database Engine error)
ms.assetid: ab95cce8-4f97-4aea-a746-a73eea7c9aab
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e779b0f514ed6892d345c2f72ecf37b8711257e3
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2018
ms.locfileid: "34329619"
---
# <a name="mssqlserver9532"></a>MSSQLSERVER_9532
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|9532|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|XMLERR_COLUMNSET_CANNOT_CONVERT_FROM_TO|  
|訊息文字|在包含資料行集 '%.*ls' 的查詢/DML 作業中，將資料行 '%.\*ls' 從資料類型 '%ls' 轉換成資料類型 '%ls' 時，轉換失敗。|  
  
## <a name="explanation"></a>說明  
資料行集是不具類型的 XML 表示，可將資料表的某些資料行結合到結構化輸出中。 當您透過 XML 資料行集來插入或更新疏鬆資料行值時，插入基礎疏鬆資料行內的值會從 **xml** 資料類型隱含地轉換。 提供了無法轉換成此資料行之資料類型的值。  
  
## <a name="user-action"></a>使用者動作  
由於提供的值無法隱含地轉換，所以它可能是無效的輸入。 請更正錯誤後重試。 如果此值正確無誤，請修改陳述式來使用個別資料行，而非資料行集。 如此可讓您明確地將此值轉換成正確的資料類型。  
  
