---
title: "SQLFetch （資料指標程式庫） |Microsoft 文件"
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
- SQLFetch function [ODBC], Cursor Library
ms.assetid: 35a0d493-778b-4fb1-84ee-a13540e2fe0e
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1e5cabca53c503e2cd0c12147248b11da84ed157
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="sqlfetch-cursor-library"></a>SQLFetch （資料指標程式庫）
> [!IMPORTANT]  
>  將移除這項功能，在未來的版本的 Windows。 避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 Microsoft 建議使用驅動程式的資料指標功能。  
  
 本主題討論使用**SQLFetch**資料指標程式庫中的函式。 如需一般資訊**SQLFetch**，請參閱[SQLFetch 函數](../../../odbc/reference/syntax/sqlfetch-function.md)。  
  
 使用資料指標程式庫時，呼叫**SQLFetch**不得與呼叫**SQLFetchScroll**或**SQLExtendedFetch**。  
  
 如果**SQLFetch**呼叫使用 SQL_ATTR_ROW_ARRAY_SIZE 設定為大於 1，資料指標程式庫會傳遞至驅動程式呼叫。 如果驅動程式的 ODBC 2。*x*驅動程式，將略過資料列集大小，並呼叫， **SQLFetch**會傳回單一資料列。  
  
 如果資料指標程式庫會使用 ODBC 2。*x*沒有驅動程式，位移 （以 SQL_ATTR_ROW_BIND_OFFSET_PTR 陳述式屬性來定義） 的繫結時使用**SQLFetch**呼叫。  
  
 應用程式載入資料指標程式庫時，無法呼叫**SQLFetch**擷取書籤資料行。 資料指標程式庫會傳遞至呼叫**SQLFetch**透過驅動程式，但函式呼叫啟用書籤和書籤資料行繫結會攔截資料指標程式庫。
