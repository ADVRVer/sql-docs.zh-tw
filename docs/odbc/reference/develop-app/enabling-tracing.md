---
title: 啟用追蹤 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], enabling
ms.assetid: 48e318bd-2487-4708-a698-ea01f36a45e9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fb6d8eaf4a1f4eaadc4e8e9a7030b81c373d8377
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47819916"
---
# <a name="enabling-tracing"></a>啟用追蹤
追蹤可以啟用下列三種方式：  
  
-   設定**追蹤**並**TraceFile** Odbc.ini 登錄項目中的關鍵字。 這會啟用或停用追蹤時**SQLAllocHandle**具有*HandleType*利用 SQL_HANDLE_ENV 的呼叫。 在 資料來源的安裝過程中顯示的 ODBC 資料來源管理員 對話方塊中的 追蹤 索引標籤中設定這些選項。 如需詳細資訊，請參閱 <<c0> [ 資料來源的登錄項目](../../../odbc/reference/install/registry-entries-for-data-sources.md)。  
  
-   呼叫**SQLSetConnectAttr**設 SQL_OPT_TRACE_ON SQL_ATTR_TRACE 連接屬性。 這會啟用或停用連線的持續時間的追蹤。 如需詳細資訊，請參閱 < [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)函式描述。  
  
-   使用**ODBCSharedTraceFlag**若要開啟或關閉追蹤以動態方式。 (如需詳細資訊，請參閱下一個主題中，[動態追蹤](../../../odbc/reference/develop-app/dynamic-tracing.md)。)
