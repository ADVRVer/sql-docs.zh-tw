---
title: "SQLFreeStmt （資料指標程式庫） |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLFreeStmt function [ODBC], Cursor Library
ms.assetid: 47bfbd4d-9453-4609-958d-1e05794cb223
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b648c069c3930e923db8a929f7203807c67b128e
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="sqlfreestmt-cursor-library"></a>SQLFreeStmt （資料指標程式庫）
> [!IMPORTANT]  
>  將移除這項功能，在未來的版本的 Windows。 避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 Microsoft 建議使用驅動程式的資料指標功能。  
  
 本主題討論使用**SQLFreeStmt**資料指標程式庫中的函式。 如需一般資訊**SQLFreeStmt**，請參閱[SQLFreeStmt 函數](../../../odbc/reference/syntax/sqlfreestmt-function.md)。  
  
 如果應用程式呼叫**SQLFreeStmt**使用 SQL_UNBIND 選項之後，它會呼叫**SQLExtendedFetch**， **SQLFetch**，或**SQLFetchScroll**，資料指標程式庫會傳回錯誤。 它可以解除繫結結果集資料行之前，應用程式必須先呼叫**SQLCloseCursor**或**SQLFreeStmt** SQL_CLOSE 選項。
