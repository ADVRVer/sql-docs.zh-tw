---
title: "驅動程式的角色 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- driver error checking [ODBC]
- diagnostic information [ODBC], driver error checking
ms.assetid: cac64c24-a27d-4884-96c0-ea7988351711
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2fe0d0545bcc787275bda3ba2154088f23eeda20
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="role-of-the-driver"></a>驅動程式的角色
驅動程式會檢查所有錯誤和警告不會檢查驅動程式管理員，並排序它所產生的狀態記錄。 資料庫連接 (ODBC 2。*x*驅動程式不會排序狀態記錄。)這在資料截斷、 資料轉換、 語法和某些狀態轉換包含錯誤和警告。 錯誤和警告部分核取驅動程式管理員，可能也會檢查驅動程式。 例如，雖然驅動程式管理員會檢查是否值*作業*中**SQLSetPos**是合法的驅動程式必須檢查它是否支援。  
  
 驅動程式也會對應*原生錯誤*— 也就是資料來源傳回的錯誤 — 以 Sqlstate。 例如，驅動程式可能對應不合法 SQL 語法以 SQLSTATE 42000 （語法錯誤或存取違規） 不同的原生錯誤的號碼。 驅動程式會傳回自發性錯誤號碼 SQL_DIAG_NATIVE 欄位中的狀態記錄。 驅動程式文件應該會顯示如何錯誤和警告對應資料來源中的引數**SQLGetDiagRec**和**SQLGetDiagField**。

