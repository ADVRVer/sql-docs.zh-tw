---
title: 依序數載入 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], loading by ordinal
- compatibility [ODBC], loading by ordinal
- loading by ordinal [ODBC]
ms.assetid: 337d90ab-68eb-4940-a2f3-f7d5693ee766
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 702e1fe58080cc370ab9a858c985a7744df85050
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47845856"
---
# <a name="loading-by-ordinal"></a>依序數載入
在 ODBC 2。*x*，無法執行依序數載入，以改善連線程序的效能。 ODBC 2。*x*驅動程式匯出序數 199 虛擬函式; 當驅動程式管理員偵測到它，序數，而不使用名稱解析的 ODBC 函式的位址。 這項功能仍然支援 ODBC 2。*x*驅動程式，但不是支援 ODBC 3 *.x*驅動程式。
