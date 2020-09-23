---
title: 改善 JDBC 驅動程式的效能與可靠性
description: 了解使用 Microsoft JDBC Driver for SQL Server 時，可改善應用程式效能和可靠性的各種技術。
ms.custom: ''
ms.date: 07/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e1592499-b87b-45ee-bab8-beaba8fde841
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bc04a90569974acbc99dcb66680d66289db1c0d1
ms.sourcegitcommit: b80364e31739d7b08cc388c1f83bb01de5dd45c1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87565376"
---
# <a name="improving-performance-and-reliability-with-the-jdbc-driver"></a>改善 JDBC 驅動程式的效能與可靠性

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

所有應用程式在應用程式開發上皆通用的一個概念即需要不斷地增進效能與可靠性。 有一些技術可以用在 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]，以達成此目的。  
  
本節的主題說明當使用 JDBC 驅動程式時，可改善應用程式效能和可靠性的各種技術。  

## <a name="in-this-section"></a>本節內容

|主題|描述|  
|-----------|-----------------|  
|[不使用時關閉物件](../../connect/jdbc/closing-objects-when-not-in-use.md)|說明不再需要 JDBC 驅動程式物件時，關閉它們的重要性。|  
|[管理交易大小](../../connect/jdbc/managing-transaction-size.md)|說明增進交易效能的技術。|  
|[使用陳述式及結果集](../../connect/jdbc/working-with-statements-and-result-sets.md)|描述使用陳述式或 ResultSet 物件時，用來改善效能的技術。|  
|[使用自適性緩衝](../../connect/jdbc/using-adaptive-buffering.md)|描述適應性緩衝功能，這項功能設計成可擷取任何種類的大數值資料，而不會造成伺服器資料指標的負擔。|  
|[疏鬆資料行](../../connect/jdbc/sparse-columns.md)|討論 JDBC 驅動程式對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 疏鬆資料行的支援。|  
|[JDBC 驅動程式的備妥陳述式中繼資料快取](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)|討論使用備妥的陳述式查詢來改善效能的技巧。|
|[使用大量複製 API 執行批次插入作業](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md)|說明如何針對批次插入作業與其優點啟用「大量複製 API」功能。|
|[不以 Unicode 的形式傳送 String 參數](../../connect/jdbc/setting-the-connection-properties.md)|處理 **CHAR**、**VARCHAR** 與 **LONGVARCHAR** 資料時，使用者可以將 **sendStringParametersAsUnicode** 連線屬性設定為 `false` 來獲得最佳效能提升。|

## <a name="see-also"></a>另請參閱

[JDBC 驅動程式概觀](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
