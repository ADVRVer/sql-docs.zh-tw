---
title: "中斷並重新連接的資料錄集 |Microsoft 文件"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Recordset object [ADO], disconnecting and reconnecting
ms.assetid: c5134af7-81d6-4de4-9fd1-cfe29973545e
caps.latest.revision: "4"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 761b1e37cd8f51e53bc486de460f43212d33df1a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="disconnecting-and-reconnecting-the-recordset"></a>中斷並重新連接的資料錄集
開啟資料來源的用戶端的資料錄集，然後中斷資料來源中的資料錄集的功能最強大的功能在 ADO 中找到的其中一個。 一旦已中斷連接資料錄集，可以被關閉資料來源的連接，藉此釋放用來進行維護的伺服器上的資源。 您可用來檢視和編輯資料錄集中的資料，它已中斷連接時繼續並稍後重新連線至資料來源和批次模式中傳送您的更新。  
  
 若要中斷資料錄集，開啟 adUseClient，資料指標位置，然後設定 ActiveConnection 屬性等於執行任何動作。 （c + + 使用者應該設定 ActiveConnection 等於 NULL 中斷連線）。  
  
 我們已中斷連線的資料錄集稍後時要使用這一節我們將討論解決案例，我們要在用戶端電腦未連線到網路時，具有資料應用程式可使用資料錄集中的資料錄集持續性。  
  
## <a name="see-also"></a>請參閱＜  
 [批次模式](../../../ado/guide/data/batch-mode.md)
