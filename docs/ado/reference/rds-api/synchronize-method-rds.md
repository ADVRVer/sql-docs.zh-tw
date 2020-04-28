---
title: Synchronize 方法（RDS） |Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Synchronize method [ADO]
ms.assetid: 7af42866-7db2-4174-8251-388a2cf741f2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e280e5f8c9eda472c6448b199ffa94ac18c13751
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "67963269"
---
# <a name="synchronize-method-rds"></a>Synchronize 方法 (RDS)
將指定的記錄集與連接字串所指定的資料庫同步處理，以便在 ADO 2.5 和更新版本中使用。  
  
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，Windows 作業系統不再包含 RDS 伺服器元件（如需詳細資訊，請參閱 Windows 8 和[Windows Server 2012 相容性操作手冊](https://www.microsoft.com/download/details.aspx?id=27416)）。 RDS 用戶端元件將會在未來的 Windows 版本中移除。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該遷移至[WCF 資料服務](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="syntax"></a>語法  
  
```  
  
object.Synchronize(ConnectionString As String, HandlerString As String, lSynchronizeOptions As Long, ppRecordset As Object, pStatusArray, [lcid As Long], [pInformation)  
```  
  
#### <a name="parameters"></a>參數  
 *ConnectionString*  
 用來連接到要求將傳送至其中之 OLE DB 提供者的字串。 如果使用處理程式，處理常式可能會編輯或取代連接字串。  
  
 *HandlerString*  
 字串會識別要與此執行搭配使用的處理常式。 此字串包含兩個部分。 第一個部分包含要使用之處理常式的名稱（ProgID）。 字串的第二個部分包含要傳遞至處理常式的引數。 引數字串的解讀方式是處理常式特有的。 這兩個部分會以字串中的第一個逗號實例分隔（雖然引數字串可能包含額外的逗號）。 引數是選擇性的。  
  
 *lSynchronizeOptions*  
 同步處理選項的位元遮罩。  
  
 1 = 資料庫的*UpdateTransact*更新會包裝在交易中。 若有任何更新失敗，則會中止交易。  
  
 2 = 當未設定*Refresh*或*RefreshConflicts*時，*RefreshWithUpdate*會導致傳回資料列狀態。  
  
 4 =*重新*整理記錄集時，會使用資料庫中的目前資料進行重新整理。 暫止的更新不會推送到資料庫。 如果未設定此位，就不會重新整理記錄集，而且任何暫止的更新都會推送至資料庫。  
  
 8 =*RefreshConflicts*任何具有暫止變更的資料列都無法更新。 無法更新的資料列會以資料庫中的目前資料進行重新整理。  
  
 *ppRecordset*  
 要同步處理之記錄集的指標。  
  
 *pStatusArray*  
 Variant，用來針對受同步處理影響的資料列，傳回資料列狀態的安全陣列。 如果未設定下列同步處理選項，則未設定： *RefreshWithUpdate*、 *Refresh*和*RefreshConflicts*。  
  
 *lcid*  
 用來建立*pInformation*中所傳回之任何錯誤的 LCID。  
  
 *pInformation*  
 **Execute**所傳回之資訊錯誤的指標。 如果是 Null，則不會傳回任何錯誤資訊。  
  
## <a name="remarks"></a>備註  
 *HandlerString*參數可以是 null。 在此情況下，會發生的情況取決於 RDS 伺服器的設定方式。 "MSDFMAP" 的處理常式字串表示應該使用 Microsoft 提供的處理常式（Msdfmap）。 "MASDFMAP" 處理常式字串 "Msdfmap" 表示應該使用處理程式，而且應該將引數 "sample" 傳遞給處理常式。 然後，Msdfmap 會將引數解讀為使用範例 .ini 來檢查連接和查詢字串的方向。  
  
## <a name="applies-to"></a>套用至  
 [DataFactory 物件 (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


