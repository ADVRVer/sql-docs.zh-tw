---
title: "了解 JDBC Driver 資料類型 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7802328d-4d23-4775-9573-4169b127d258
caps.latest.revision: "27"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 1c9599a6e71ee0fbf171ba9c8619cafac8332cc5
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="understanding-the-jdbc-driver-data-types"></a>了解 JDBC Driver 資料類型
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]支援 JDBC 基本和進階資料類型使用的 Java 應用程式內使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]當做其資料庫。  
  
 JDBC 類型系統會調解之間的轉換[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]資料類型和 Java 語言類型與物件。 JDBC 類型的模型是以 SQL-92 和 SQL-99 類型建立的。 JDBC 驅動程式遵守 JDBC 規格，其設計在於提供可預測性與彈性之間的正確平衡。  
  
 本節中的主題描述如何使用基本和進階資料類型，以及如何將資料類型轉換為其他資料類型。  
  
## <a name="in-this-section"></a>本節內容  
  
|主題|Description|  
|-----------|-----------------|  
|[使用基本資料類型](../../connect/jdbc/using-basic-data-types.md)|描述 JDBC 基本資料類型。 包括如何透過結果集、參數化查詢以及預存程序來使用資料類型的範例。|  
|[設定 java.sql.Time 值如何傳送給伺服器](../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)|描述 JDBC 驅動程式產生日期的方式。|  
|[使用進階資料類型](../../connect/jdbc/using-advanced-data-types.md)|描述 JDBC 進階資料類型。|  
|[了解資料類型差異](../../connect/jdbc/understanding-data-type-differences.md)|描述各種 JDBC 驅動程式資料類型之間的差異。|  
|[了解資料類型轉換](../../connect/jdbc/understanding-data-type-conversions.md)|描述在使用 getter 和 setter 方法時，如何處理資料類型轉換。|  
|[國家字元集支援](../../connect/jdbc/national-character-set-support.md)|描述國家字元集類型的支援。|  
|[支援 XML 資料](../../connect/jdbc/supporting-xml-data.md)|描述 SQLXML 介面。 同時描述如何讀取和寫入 XML 資料的關聯式資料庫，使用**SQLXML** Java 資料類型。|  
|[包裝函式與介面](../../connect/jdbc/wrappers-and-interfaces.md)|討論擁有介面[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]特有方法與常數，讓應用程式伺服器建立的 proxy 類別，也會討論支援 java.sql.Wrapper 介面。|  
  
## <a name="see-also"></a>請參閱＜  
 [JDBC Driver 概觀](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
