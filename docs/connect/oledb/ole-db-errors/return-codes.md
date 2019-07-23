---
title: 傳回碼 |Microsoft Docs
description: 傳回碼
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB error handling, return codes
- OLE DB Driver for SQL Server, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
author: pmasl
ms.author: pelopes
ms.openlocfilehash: a1deedd8903f69268ebc5e7f5caafaa79a7f7b18
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67994932"
---
# <a name="return-codes"></a>傳回碼
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  在大部分的基本層級，成員函數不是成功就是失敗。 在更精確一點的層級，函數可能會成功，但是其成功可能不是應用程式開發人員所樂見的。  
  
 如需 OLE DB 傳回碼的詳細資訊，請參閱 [Return Codes (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631) (傳回碼 (OLE DB))。  
  
 當 SQL Server 成員函式的 OLE DB 驅動程式傳回 S_OK 時, 函數會成功。  
  
 當 OLE DB Driver for SQL Server 成員函式沒有傳回 S_OK 時，OLE/COM HRESULT 解開的 FAILED 和 IS_ERROR 巨集可以決定函式的整體成功或失敗。  
  
 如果 FAILED 或 IS_ERROR 傳回 TRUE，OLE DB Driver for SQL Server 取用者可確保成員函式執行失敗。 當 FAILED 或 IS_ERROR 傳回 FALSE, 而且 HRESULT 不等於 S_OK 時, SQL Server 取用者的 OLE DB 驅動程式可確保函數在某種意義下成功。 取用者可以擷取從 OLE DB Driver for SQL Server 錯誤介面傳回的這個「條件式成功」(Success with Information) 的詳細資訊。 同時，在函式清楚地失敗 (FAILED 巨集會傳回 TRUE) 的情況下，可從 OLE DB Driver for SQL Server 錯誤介面取得擴充的錯誤資訊。  
  
 SQL Server 取用者 OLE DB 驅動程式通常會遇到「資訊成功」的 DB_S_ERRORSOCCURRED HRESULT 傳回。 傳回 DB_S_ERRORSOCCURRED 的成員函數通常會定義一或多個可提供狀態值給取用者的參數。 取用者無法取得在狀態值參數中傳回之錯誤資訊以外的錯誤資訊，因此取用者應該在可取得錯誤資訊時，實作應用程式邏輯來擷取狀態值。  
  
 SQL Server 成員函式的 OLE DB 驅動程式不會傳回成功的錯誤碼 S_FALSE。 SQL Server 成員函式的所有 OLE DB 驅動程式一律會傳回 S_OK 來表示成功。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤](../../oledb/ole-db-errors/errors.md)  
  
  
