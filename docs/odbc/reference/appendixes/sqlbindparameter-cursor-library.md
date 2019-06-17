---
title: SQLBindParameter （資料指標程式庫） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindParameter function [ODBC], Cursor Library
ms.assetid: 04c53e4c-cd1d-40b2-9997-684ebe43499f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eafab0f29cb4e1b7ecdfea378f9315ba29cf133f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199679"
---
# <a name="sqlbindparameter-cursor-library"></a>SQLBindParameter (資料指標程式庫)
> [!IMPORTANT]  
>  Windows 的未來版本將移除這項功能。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 Microsoft 建議使用驅動程式的資料指標功能。  
  
 本主題討論使用**SQLBindParameter**資料指標程式庫中的函式。 如需一般資訊**SQLBindParameter**，請參閱[SQLBindParameter 函式](../../../odbc/reference/syntax/sqlbindparameter-function.md)。  
  
 應用程式可以呼叫**SQLBindParameter**重新繫結參數，只要 C 資料類型、 資料行大小和小數位數的繫結的資料行維持不變。  
  
 資料指標程式庫支援 SQL_ATTR_ROW_BIND_OFFSET_PTR 陳述式將屬性設定為使用繫結的位移。 (**SQLBindParameter**並沒有為此重新繫結進行呼叫。)  
  
 資料指標程式庫支援繫結的資料在執行中參數。
