---
title: "算術錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a0a24a87c814c51bcf3270298b56b5ffec01fa29
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="arithmetic-errors"></a>算術錯誤
ODBC 驅動程式會評估中的 SELECT 陳述式的 WHERE 子句，因為它會擷取每個資料列。 如果資料列包含一個值，會導致算術錯誤，例如除以零或數字溢位，驅動程式傳回所有資料列，但傳回的資料行的算術錯誤的錯誤。 當插入或更新，不過，ODBC 驅動程式會停止插入或更新資料，在遇到第一個的算術錯誤時。
