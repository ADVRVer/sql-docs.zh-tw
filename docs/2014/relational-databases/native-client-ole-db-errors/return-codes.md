---
title: 傳回碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB error handling, return codes
- SQL Server Native Client OLE DB provider, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
ms.assetid: 7f7457e9-fce4-400c-82e5-ee02e9e811c6
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 37f3326aacd601dd9b52f0f55e146fa1b17cdcc7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36022157"
---
# <a name="return-codes"></a>傳回碼
  在大部分的基本層級，成員函數不是成功就是失敗。 在更精確一點的層級，函數可能會成功，但是其成功可能不是應用程式開發人員所樂見的。  
  
 如需有關 OLE DB 傳回碼的詳細資訊，請參閱[傳回碼 (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=101631)。  
  
 當[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者成員函數傳回 S_OK 時，該函數會成功。  
  
 當[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者成員函數沒有傳回 S_OK 時，OLE/COM HRESULT 解開的 FAILED 和 IS_ERROR 巨集可以決定整體成功或失敗函式。  
  
 如果 FAILED 或 IS_ERROR 傳回 TRUE， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者取用者可確保成員函數執行失敗。 當 FAILED 或 IS_ERROR 傳回 FALSE，而且 HRESULT 不等於 S_OK 時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者取用者可確保函數在某種意義上會成功。 取用者可以擷取從傳回在此 「 成功資訊 」 的詳細的資訊[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者錯誤介面。 此外，在函數清楚地失敗 （FAILED 巨集會傳回 TRUE） 的情況下，擴充的錯誤資訊位於[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者錯誤介面。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者取用者通常會使用資訊的 DB_S_ERRORSOCCURRED 「 成功 」 的 HRESULT 傳回。 傳回 DB_S_ERRORSOCCURRED 的成員函數通常會定義一或多個可提供狀態值給取用者的參數。 取用者無法取得在狀態值參數中傳回之錯誤資訊以外的錯誤資訊，因此取用者應該在可取得錯誤資訊時，實作應用程式邏輯來擷取狀態值。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者成員函數不會傳回成功碼 S_FALSE。 所有[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者成員函數一律傳回 S_OK 來表示成功。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤](errors.md)  
  
  