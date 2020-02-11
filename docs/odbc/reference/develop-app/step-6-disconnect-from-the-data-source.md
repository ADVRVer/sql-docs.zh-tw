---
title: 步驟6：中斷與資料來源的連線 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], disconnecting from data source
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
ms.assetid: 6ad759ba-4721-4d8f-9b26-de976d4fc1a0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 65cc2ae8d2c2248a733e6efa9537fd3b40bb8fd1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114115"
---
# <a name="step-6-disconnect-from-the-data-source"></a>步驟 6：中斷與資料來源的連線
最後一個步驟是中斷與資料來源的連線，如下圖所示。 首先，應用程式會藉由呼叫**SQLFreeHandle**來釋放任何語句控制碼。 如需詳細資訊，請參閱[釋放語句控制碼](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md)。  
  
 ![顯示中斷連接資料來源](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 接下來，應用程式會使用**SQLDisconnect**從資料來源中斷連線，並釋放與**SQLFreeHandle**的連接控制碼。 如需詳細資訊，請參閱[從資料來源或驅動程式中斷連接](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md)。  
  
 最後，應用程式會使用**SQLFreeHandle**釋出環境控制碼，並卸載驅動程式管理員。 如需詳細資訊，請參閱配置[環境控制碼](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)。
