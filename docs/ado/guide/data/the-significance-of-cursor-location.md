---
title: 資料指標位置的重要性 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- server-side cursors [ADO]
- cursors [ADO], client-side
- client-side cursors [ADO]
- cursors [ADO], server-side
ms.assetid: 70ef5b1c-0459-41a1-b796-031f61a29a8a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d25153a3c84340ad6feea43aa969ef52d358fe4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47717716"
---
# <a name="the-significance-of-cursor-location"></a>資料指標位置的精確度
每個資料指標會使用暫存的資源，來保留資料。 這些資源可以是記憶體、 磁碟分頁檔案、 暫存磁碟的檔案或甚至是暫時儲存在資料庫中。 資料指標稱為*用戶端*時這些資源位於用戶端電腦上的資料指標。 資料指標稱為*伺服器端*時這些資源位於伺服器上的資料指標。  
  
## <a name="client-side-cursors"></a>用戶端資料指標  
 在 ADO 中，呼叫用戶端資料指標所使用**adUseClient CursorLocationEnum。** 使用非索引鍵集用戶端資料指標，伺服器會傳送整個結果集在網路上用戶端電腦。 用戶端電腦提供和管理的資料指標或結果集所需的暫存資源。 用戶端應用程式可以瀏覽整個結果集來判斷需要哪些資料列。  
  
 靜態和索引鍵集導向的用戶端資料指標可能很大的負擔，您的工作站上，如果它們包含太多資料列。 雖然所有的資料指標程式庫能夠建置與數千個資料列的資料指標時，設計來擷取這類大型的資料列集的應用程式可能不佳。 當然也有例外狀況。 對於某些應用程式中，大型的用戶端資料指標可能非常恰當，效能可能不會產生問題。  
  
 用戶端資料指標的其中一個明顯的優點是快速的回應。 結果集已下載至用戶端電腦之後，瀏覽資料列是非常快速。 您的應用程式是通常更具擴充性與用戶端資料指標，因為每個個別的用戶端和伺服器上找不到放置游標的資源需求。  
  
## <a name="server-side-cursors"></a>伺服器端資料指標  
 在 ADO 中呼叫伺服器端資料指標所使用**adUseServer CursorLocationEnum。** 使用伺服器端資料指標中，伺服器會管理結果集使用的伺服器電腦所提供的資源。 伺服器端資料指標會透過網路傳回要求的資料。 這種類型的資料指標有時可以提供較佳的效能比用戶端資料指標，尤其是在網路流量過大的問題的情況。  
  
 不過，請務必指出伺服器端資料指標是 — 至少要暫時 — 針對每個作用中的用戶端耗用寶貴的伺服器資源。 若要確保您的伺服器硬體能夠管理所有作用中的用戶端要求的伺服器端資料指標必須據此進行規劃。 此外，因為它會提供只有單一資料列的權限的伺服器端資料指標可能會很慢，沒有可用的批次資料指標。  
  
 伺服器端資料指標是插入、 更新或刪除記錄時很有用的。 與伺服器端資料指標，您可以在相同連接上有多個作用中陳述式。
