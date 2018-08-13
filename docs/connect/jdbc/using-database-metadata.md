---
title: 使用資料庫中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8b048371-e912-4ed1-afd7-436978f48888
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bf9fd776fc14c060d5624d704efc315cc04da85f
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39661640"
---
# <a name="using-database-metadata"></a>使用資料庫中繼資料

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

為了查詢資料庫中有關其支援之項目的資訊，[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 會實作 [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) 類別。 此類別包含數種方法，會以單一值形式或以結果集傳回資訊。

若要建立 SQLServerDatabaseMetaData 物件，您可以使用 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) 類別的 [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md) 方法來取得有關它連線之資料庫的資訊。

在下列範例中，開啟連線[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]範例資料庫會傳遞至函式、 SQLServerConnection 類別的 getMetaData 方法來傳回 SQLServerDatabaseMetadata 物件，並接著的各種方法SQLServerDatabaseMetaData 物件用來顯示驅動程式、 驅動程式版本、 資料庫名稱和資料庫版本的相關資訊。

[!code[JDBC#UsingDBMetaData1](../../connect/jdbc/codesnippet/Java/using-database-metadata_1.java)]

## <a name="see-also"></a>另請參閱

[使用 JDBC Driver 處理中繼資料](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)
