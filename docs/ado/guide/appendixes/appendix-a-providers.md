---
title: 附錄 a： 提供者 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data providers [ADO]
- providers [ADO]
- ADO, providers
- service providers [ADO]
- service components [ADO]
ms.assetid: e2581b47-b11e-4e1e-b96c-d39c77c5b48a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5110c06913325421aeeaa2d31295d7e2bc6bf59c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645596"
---
# <a name="appendix-a-data-and-service-providers"></a>附錄 a： 資料和服務提供者
本節說明三種類型的提供者： 資料提供者、 服務提供者，以及服務元件。 提供者分為兩類： 提供與資料提供服務。 A*資料提供者*擁有它自己的資料，且會公開在表格式的格式，您的應用程式。 A*服務提供者*封裝所產生和取用資料，擴充功能，ADO 應用程式中的服務。 服務提供者可能也會進一步定義成*服務元件*，這必須與其他服務提供者或元件搭配運作。

## <a name="data-providers"></a>資料提供者
 ADO 是功能強大且靈活的因為它可以連線到任何數個不同的資料提供者，並仍會公開相同的程式設計模型，不論任何指定的提供者的特定功能。

 不過，因為每個資料提供者是唯一的您的應用程式與 ADO 之間的互動方式會因稍微資料提供者。 差異通常分為三類：

-   在 連接參數[ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)屬性。

-   [命令](../../../ado/reference/ado-api/command-object-ado.md)物件使用方式。

-   提供者專屬[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)行為。

 針對每個 Microsoft 目前提供的資料提供者的詳細資料如下所列。

|區域|主題|
|----------|-----------|
|ODBC 資料庫|[Microsoft OLE DB Provider for ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)|
|Microsoft 索引服務|[Microsoft OLE DB Provider for Microsoft 索引服務](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md)|
|Active Directory 服務|[Microsoft Active Directory 服務的 Microsoft OLE DB 提供者](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md)|
|Microsoft Jet 資料庫|[Microsoft Jet OLE DB 提供者](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)|
|Microsoft SQL Server|[Microsoft OLE DB Provider for SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)|
|Oracle 資料庫|[Microsoft OLE DB Provider for Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md)|
|網際網路發佈|[適用於網際網路發佈的 Microsoft OLE DB 提供者](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)|
|簡單的資料來源|[Microsoft OLE DB 簡單提供者](../../../ado/guide/appendixes/microsoft-ole-db-simple-provider.md)|

## <a name="provider-specific-dynamic-properties"></a>提供者特有的動態屬性
 [屬性](../../../ado/reference/ado-api/properties-collection-ado.md)的集合[連線](../../../ado/reference/ado-api/connection-object-ado.md)，[命令](../../../ado/reference/ado-api/command-object-ado.md)，以及[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)物件包含特定的動態屬性提供者。 這些屬性會提供給超出 ADO 支援的內建屬性提供者特定功能的相關資訊。

 建立連線，並建立這些物件之後, 使用[重新整理](../../../ado/reference/ado-api/refresh-method-ado.md)方法**屬性**要取得提供者特定屬性之物件的集合。 請參閱提供者文件和[OLE DB 程式設計人員指南](http://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)這些動態屬性的詳細資訊。

## <a name="service-providers"></a>服務提供者
 若要使用的服務提供者，您必須提供的關鍵字。 您也應該知道的每個服務提供者相關聯的提供者特定動態屬性。 Microsoft 目前提供每個服務提供者列出提供者專屬的詳細資料：

-   [Microsoft Data Shaping Service for OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)

-   [Microsoft OLE DB 持續性提供者](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)

-   [Microsoft OLE DB 遠端服務提供者](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)

## <a name="service-components"></a>服務元件
 [OLE DB 的資料指標服務](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)服務元件的補充資料提供者的資料指標支援函式。 它也需要關鍵字，並具有動態屬性。

 如需有關 OLE DB 提供者的詳細資訊，請參閱 < [Microsoft OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx)。

## <a name="provider-commands"></a>提供者命令
 每個提供者列於此處，如果您的應用程式允許使用者輸入 SQL 陳述式的提供者命令，您必須一律驗證使用者輸入，並保持警戒使用有潛在危險的 SQL 陳述式，例如可能的駭客攻擊的`DROP TABLE t1`，使用者輸入的一部分。

## <a name="see-also"></a>另請參閱
 [命令物件 (ADO)](../../../ado/reference/ado-api/command-object-ado.md) [Connection 物件 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) [Microsoft OLE DB 提供者，適用於網際網路發佈](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md) [Microsoft Active Directory 服務的 Microsoft OLE DB 提供者](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md) [Microsoft 索引服務的 Microsoft OLE DB 提供者](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md) [Microsoft OLE DB Provider for ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md) [Microsoft OLE DB Provider for Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md) [Microsoft OLE DB Provider for SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) [Microsoft OLE DB Provider for Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) [屬性集合 (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [資料錄集物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [Refresh 方法 (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)
