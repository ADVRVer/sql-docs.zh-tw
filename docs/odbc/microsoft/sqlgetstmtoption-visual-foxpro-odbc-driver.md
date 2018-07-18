---
title: SQLGetStmtOption （Visual FoxPro ODBC 驅動程式） |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLGetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 984a8b1d-f12c-420c-8be4-f555114c764b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd943c877c9fcd99c230e3d791758cbc7d0661d2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32903983"
---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption （Visual FoxPro ODBC 驅動程式）
> [!NOTE]  
>  本主題包含 Visual FoxPro ODBC 驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC 應用程式開發介面參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 支援： 完整  
  
 ODBC 應用程式開發介面相容性： 層級的其中一個  
  
 傳回目前的陳述式選項的設定。  
  
|*fOption*|傳回值|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|32 位元整數值，是目前的記錄編號的書籤|  
|SQL_ROW_NUMBER|32 位元整數，指定目前的資料列在結果中的位置設定|  
|SQL_TRANSLATE_DLL|錯誤: 「 驅動程式不適用 」|  
  
 Visual FoxPro ODBC 驅動程式會有任何轉譯 Dll。  
  
 如需詳細資訊，請參閱[SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md)中*ODBC 程式設計人員參考*。
