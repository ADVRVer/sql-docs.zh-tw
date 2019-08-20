---
title: 不使用時關閉物件 |Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce8f9b35-c761-4b0c-9a46-985eef2c2e0b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 130b639c7a721ea48a12c7e054834da7b61ab0c7
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028357"
---
# <a name="closing-objects-when-not-in-use"></a>不使用時關閉物件
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  當您使用 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 的物件 (特別是 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) 或其中一個 Statement 物件，例如 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)、[SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) 或 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)) 時，應該在不再需要時，使用其 close 方法明確地關閉這些物件。 這樣可以盡快釋放驅動程式與伺服器資源，而不必等待 Java Virtual Machine 記憶體回收行程為您執行，藉以改善效能。  
  
 當您使用捲動鎖定時，關閉物件對於在伺服器上維持良好的並行特別重要。 在關閉結果集之前，會保留最後存取之提取緩衝區中的捲動鎖定。 同樣地，在關閉陳述式之前，會保留準備控制代碼的陳述式。 如果您要針對多個陳述式重複使用連接，在您讓這些陳述式離開範圍前關閉它們將會讓伺服器提早清除準備的控制代碼。  
  
## <a name="see-also"></a>另請參閱  
 [改善JDBC 驅動程式的效能與可靠性](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
