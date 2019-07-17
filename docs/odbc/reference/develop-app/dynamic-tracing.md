---
title: 動態追蹤 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], dynamic
- dynamic tracing [ODBC]
ms.assetid: ebe58a83-a7b0-4747-86c8-2af2940471ef
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8420589761a1f8cb1f9cf8a3022842863fd30758
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68046896"
---
# <a name="dynamic-tracing"></a>動態追蹤
追蹤可以啟用或停用在執行應用程式中的任何時間點。 這可讓應用程式，以追蹤任何數目的函式呼叫。  
  
 變數**ODBCSharedTraceFlag**設為啟用動態追蹤。 此變數會在所有執行中複本的驅動程式管理員之間共用。 如果任何應用程式會將這個變數，所有目前執行的 ODBC 應用程式啟用追蹤。 若要開啟追蹤，關閉動態追蹤已啟用時，應用程式會呼叫**SQLSetConnectAttr** SQL_ATTR_TRACE 設 SQL_TRACE_OFF。 此呼叫將會關閉該應用程式只追蹤。 使用 odbc32.lib 編譯連結的應用程式可以修改使用此變數。 追蹤資料可以顯示在即時的視窗中，而不是 ODBC 工作階段之後，必須開啟追蹤檔案。 控制項可以新增至開啟的應用程式的畫面會在追蹤開啟或關閉。  
  
 追蹤 DLL 隨附於 ODBC 3 *.x*不是安全執行緒。 不保證如果已啟用全域追蹤記錄檔將會正確地寫入 (變數**ODBCSharedTraceFlag**設定) 和多個應用程式在同一時間寫入追蹤檔案。 這種狀況不會傳回錯誤。
