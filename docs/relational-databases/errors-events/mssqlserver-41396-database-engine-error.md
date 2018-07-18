---
title: MSSQLSERVER_41396 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 41396 (Database Engine error)
ms.assetid: 4ff04042-8367-46f3-8a16-c94682d6eedb
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 27799ec8daa7964bd60220c02053b24eac4af0a7
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2018
ms.locfileid: "34319909"
---
# <a name="mssqlserver41396"></a>MSSQLSERVER_41396
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|事件識別碼|41396|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|MAX_SORT_ROWS_EXCEEDED|  
|訊息文字|排序作業超過緩衝區限制。 已中止預存程序執行。 請參閱《SQL Server 線上叢書》以取得詳細資訊。|  
  
## <a name="explanation"></a>說明  
原生編譯的預存程序會在記憶體中執行排序作業。 排序緩衝區的大小有所限制。 此錯誤表示排序緩衝區的大小超出此限制。 已中止排序作業和預存程序執行。  
  
在排序緩衝區中，每個資料列或項目的大小取決於排序的資料列數目、聯結數目以及查詢中的彙總函式數目和類型。 藉由簡化查詢，您可以縮減每個資料列的大小，進而在排序緩衝區納入更多資料列。 基底資料表中的資料列大小並不會影響排序緩衝區中每個資料列或項目的大小。  
  
## <a name="user-action"></a>使用者動作  
選取較少資料列，或是移除聯結或彙總函式以減少查詢的複雜性。  
  
## <a name="see-also"></a>另請參閱  
[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
