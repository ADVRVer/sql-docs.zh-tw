---
title: "設定 ExtendedAnsiSQL |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extendedANSISQL [ODBC], setting
ms.assetid: 37b775d1-65ac-45ac-8572-454bc4e3c1a2
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 59955db9520b409e46d179dd50fc33cedd8e15db
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2017
---
# <a name="setting-extendedansisql"></a>設定 ExtendedAnsiSQL
屬性可以控制在連接字串中，加入 ExtendedAnsiSQL 屬性：  
  
|值|Description|  
|-----------|-----------------|  
|ExtendedAnsiSQL = 0 （預設值）|此設定不會啟用新功能。|  
|ExtendedAnsiSQL = 1|此設定可讓新的功能。|  
  
 屬性也可以設定在 DSN 中，透過**進階選項**時設定 DSN 中的，透過 [控制台] 對話方塊。  
  
 將屬性設定為 0 會停用新的功能;將它設定為 1 會啟用新功能。  
  
 屬性也可以設定使用 SQLSetConnectAttr()。 屬性值是 65501 並設為 SQLINTEGER 值為 1 或 0，在上表中所述。 可以呼叫之前或之後連接，但最好是呼叫因為順序的驅動程式處理程序快取的連接屬性和連接字串連接之後。
