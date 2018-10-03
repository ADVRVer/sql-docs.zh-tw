---
title: 呼叫 SQLSetPos 以插入資料 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], inserting data
- backward compatibility [ODBC], SqlSetPos
ms.assetid: 03e5c4d0-2bb3-4649-9781-89cab73f78eb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2c7424206318436532cad62690b01427f079a589
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47819956"
---
# <a name="calling-sqlsetpos-to-insert-data"></a>呼叫 SQLSetPos 以插入資料
當 ODBC 2。*x*應用程式使用 ODBC 3 *.x*驅動程式呼叫**SQLSetPos**具有*作業*SQL_ADD，驅動程式管理員的引數不會對應至這個呼叫**SQLBulkOperations**。 如果 ODBC 3 *.x*驅動程式應該使用應用程式呼叫**SQLSetPos** SQL_ADD，與驅動程式應該支援這項操作。  
  
 一個主要的差異，在於行為時**SQLSetPos**呼叫狀態 S6 呼叫時，就會發生 SQL_ADD。 在 ODBC 2。*x*，此驅動程式傳回 S1010 時**SQLSetPos**使用中狀態 S6 SQL_ADD 呼叫 (資料指標具有已位於與之後**SQLFetch**)。 在 ODBC 3 *.x*， **SQLBulkOperations**具有*作業*SQL_ADD 可以只能以狀態 S6 呼叫。 行為中的第二個主要差異在於**SQLBulkOperations**具有*作業*SQL_ADD 可以是以狀態 S5 呼叫，而**SQLSetPos**與**作業**的 SQL_ADD 無法。 陳述式轉換，可能會發生相同的呼叫，在 ODBC 3 *.x*，請參閱[附錄 b: ODBC 狀態轉換資料表](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)。
