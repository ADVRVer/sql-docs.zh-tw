---
title: 提升效能和可靠性，JDBC 驅動程式 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e1592499-b87b-45ee-bab8-beaba8fde841
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58521cbe6c21e7ef58fc97b52e1ef6b27209e4fe
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="improving-performance-and-reliability-with-the-jdbc-driver"></a>增進 JDBC 驅動程式的效能與可靠性
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  所有應用程式在應用程式開發上皆通用的一個概念即需要不斷地增進效能與可靠性。 有一些技術以達成此[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]。  
  
 本節的主題說明當使用 JDBC 驅動程式時，可改善應用程式效能和可靠性的各種技術。  
  
## <a name="in-this-section"></a>本節內容  
  
|主題|Description|  
|-----------|-----------------|  
|[不使用時關閉物件](../../connect/jdbc/closing-objects-when-not-in-use.md)|說明不再需要 JDBC 驅動程式物件時，關閉它們的重要性。|  
|[管理交易大小](../../connect/jdbc/managing-transaction-size.md)|說明增進交易效能的技術。|  
|[使用陳述式及結果集](../../connect/jdbc/working-with-statements-and-result-sets.md)|描述使用陳述式或結果集物件時改善效能的技術。|  
|[使用適應性緩衝](../../connect/jdbc/using-adaptive-buffering.md)|描述適應性緩衝功能，這項功能設計成可擷取任何種類的大數值資料，而不會造成伺服器資料指標的負擔。|  
|[疏鬆資料行](../../connect/jdbc/sparse-columns.md)|討論 JDBC 驅動程式支援[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]疏鬆資料行。|  
|[備妥的 JDBC Driver 陳述式中繼資料快取](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)|討論使用備妥的陳述式查詢改善效能的技術。|
  
## <a name="see-also"></a>另請參閱  
 [JDBC Driver 概觀](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  