---
title: 更新 SQL Server 資料指標中的資料 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
ms.assetid: 732dafee-f2d5-4aef-aad7-3a8bf3b1e876
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: caa3f5d35d51a90809175da88c9732fd883d291d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428327"
---
# <a name="updating-data-in-sql-server-cursors"></a>更新 SQL Server 資料指標中的資料
  正在擷取和更新資料時[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料指標， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者取用者應用程式由相同的考量和條件約束套用至任何其他的用戶端應用程式所繫結。  
  
 只有在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料指標中的資料列會參與並行的資料存取控制。 取用者要求可修改的資料列集時，並行控制會由 DBPROP_LOCKMODE 所控制。 若要修改並行存取控制的層級，取用者會先設定 DBPROP_LOCKMODE 屬性，然後再開啟資料列集。  
  
 如果用戶端應用程式設計讓交易長時間保持開啟狀態，交易隔離等級可能會對資料列定位造成重大落後。 根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會使用 DBPROPVAL_TI_READCOMMITTED 所指定的讀取認可隔離等級。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料列集並行唯讀時，Native Client OLE DB 提供者支援中途讀取的隔離。 因此，取用者可以在可修改的資料列集中要求較高的隔離等級，但是無法成功要求任何較低的等級。  
  
## <a name="immediate-and-delayed-update-modes"></a>立即和延遲更新模式  
 在立即更新模式中，每個呼叫**irowsetchange:: Setdata**造成往返[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 如果取用者會將多項變更對單一資料列，會使用單一的所有變更送出更有效率**SetData**呼叫。  
  
 在延遲的更新模式中，需往返[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]針對每個資料列所示*cRows*並*rghRows*參數**irowsetupdate:: Update**。  
  
 在任一種模式下，當資料列集沒有開啟任何交易物件時，往返代表不同的交易。  
  
 當您使用**irowsetupdate:: Update**，則[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會嘗試處理每個指示的資料列。 針對任何資料列不會停止，因為無效的資料、 長度或狀態值值發生錯誤[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者處理。 參與更新的其他所有資料列或沒有任何資料列可能會遭到修改。 取用者必須檢查傳回*Prgrowstatus&lt*陣列來判斷是否有任何特定資料列時[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者傳回 DB_S_ERRORSOCCURRED。  
  
 取用者不應該假設資料列會以任何特定順序處理。 如果取用者需要透過一個以上的單一資料列進行資料修改的排序處理，取用者應該以應用程式邏輯建立該順序，並開啟交易來包含程序。  
  
## <a name="see-also"></a>另請參閱  
 [更新資料列集中的資料](updating-data-in-rowsets.md)  
  
  
