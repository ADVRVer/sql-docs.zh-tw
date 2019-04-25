---
title: 可捲動資料指標和交易隔離 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- isolation levels [ODBC]
- scrollable cursors [ODBC]
- transaction isolation [ODBC]
- transactions [ODBC], isolation
ms.assetid: f0216f4a-46e3-48ae-be0a-e2625e8403a6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5510eb58315f70195eb40390edec1766c350fb6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62468588"
---
# <a name="scrollable-cursors-and-transaction-isolation"></a>可捲動的資料指標和交易隔離
下表列出控管的可見性變更的因素。  
  
|所做的變更：|可見性取決於：|  
|----------------------|----------------------------|  
|資料指標|資料指標類型，資料指標實作|  
|在相同交易中的其他陳述式|資料指標類型|  
|其他交易中的陳述式|資料指標類型，交易隔離等級|  
  
 這些因素會在下圖中顯示。  
  
 ![控管的可見性變更的因素](../../../odbc/reference/develop-app/media/pr23.gif "pr23")  
  
 下表摘要說明每個資料指標類型的偵測由本身、 其自己的交易中其他的作業和其他交易所變更的能力。 第二個變更的可見性取決於資料指標類型和包含資料指標交易隔離等級。  
  
|資料指標 type\action|Self|擁有<br /><br /> 交易|其他<br /><br /> 交易<br /><br /> (RU[a])|其他<br /><br /> 交易<br /><br /> (RC[a])|其他<br /><br /> 交易<br /><br /> (RR[a])|其他<br /><br /> 交易<br /><br /> (S[a])|  
|-------------------------|----------|-----------------|----------------------------------|----------------------------------|----------------------------------|---------------------------------|  
|Static|||||||  
|Insert|Maybe[b]|否|否|否|否|否|  
|Update|Maybe[b]|否|否|否|否|否|  
|DELETE|Maybe[b]|否|否|否|否|否|  
|索引鍵集導向的資料指標|||||||  
|Insert|Maybe[b]|否|否|否|否|否|  
|Update|是|是|是|是|否|否|  
|DELETE|Maybe[b]|是|是|是|否|否|  
|動態|||||||  
|Insert|是|是|是|是|是|否|  
|Update|是|是|是|是|否|否|  
|DELETE|是|是|是|是|否|否|  
  
 [a] 括號括住的字母表示包含資料指標; 之交易的隔離等級（在其中進行變更） 另一筆交易的隔離等級無關。  
  
 RU:讀取未認可  
  
 RC:讀取認可  
  
 RR:可重複讀取  
  
 S:可序列化  
  
 [b] 取決於資料指標的實作方式。 資料指標是否可以偵測到這類變更透過 SQL_STATIC_SENSITIVITY 選項中會回報**SQLGetInfo**。
