---
title: SQL Server Native Client 程式設計 |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLNCLI, about SQL Server Native Client
- SQL Server Native Client, about SQL Server Native Client
- data access [SQL Server Native Client], about SQL Server Native Client
- data access [SQL Server Native Client]
- SQL Server Native Client
- SQLNCLI
- native data access [SQL Server Native Client]
ms.assetid: 14ba2cb1-a424-4e4d-b224-0bf1015ab801
caps.latest.revision: 66
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d67aec2d94399da48314a948251a5b6cd383290e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-native-client-programming"></a>SQL Server Native Client 程式設計
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 是用於 OLE DB 和 ODBC 的獨立資料存取應用程式開發介面 (API) (在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中導入)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 將 SQL OLE DB 提供者和 SQL ODBC 驅動程式結合為單一的原生動態連結程式庫 (DLL)。 此介面也提供遠超過 Windows Data Access Components (Windows DAC，之前稱為 Microsoft Data Access Components，或稱 MDAC) 的新功能。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 可用於建立新的應用程式，或者加強需要利用 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 所推出之新功能 (例如，Multiple Active Result Set (MARS)、使用者定義資料類型 (UDT)、查詢通知、快照集隔離和 XML 資料類型支援) 的現有應用程式。  
  
> [!NOTE]  
>  如需清單之間的差異[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]原生用戶端和 Windows DAC，加上有關問題的資訊來更新 Windows DAC 應用程式之前，請考慮[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]原生用戶端，請參閱[更新 SQL Server 的應用程式原生用戶端從 MDAC](../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md)。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式一定會配合 Windows DAC 所提供的 ODBC 驅動程式管理員使用。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者可以配合 Windows DAC 所提供的 OLE DB Core Services 使用，但這並非必要條件；是否使用 Core Services 是依個別應用程式的需求而定 (例如，是否需要連接共用)。  
  
 ActiveX Data Object (ADO) 應用程式可能使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者，但建議使用 ADO 搭配**DataTypeCompatibility**連接字串關鍵字 （或其對應的**資料來源**屬性)。 使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者時，ADO 應用程式可以利用 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 所推出的新功能，這些新功能可透過連接字串關鍵字或 OLE DB 屬性或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，透過 [!INCLUDE[tsql](../../includes/tsql-md.md)] 來使用。 如需有關使用搭配 ADO 使用這些功能，請參閱[使用 ADO 搭配 SQL Server Native Client](../../relational-databases/native-client/applications/using-ado-with-sql-server-native-client.md)。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 的設計目的是提供簡化的方式，讓您使用 OLE DB 或 ODBC 取得 SQL Server 的原生資料存取權。 這種方式的簡化之處在於將 OLE DB 和 ODBC 技術結合成一個程式庫，提供一種方法來改革及發展新的資料存取功能，而不需要變更目前的 Windows DAC 元件 (這些元件現在已經是 Microsoft Windows 平台的一部分)。  
  
 雖然 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 會使用 Windows DAC 中的元件，但它並非明確相依於特定的 Windows DAC 版本。 您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 搭配 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 所支援之任何作業系統安裝的 Windows DAC 版本。  
  
## <a name="in-this-section"></a>本節內容  
 [SQL Server Native Client](../../relational-databases/native-client/sql-server-native-client.md)  
 列出全新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 功能。  
  
 [使用 SQL Server Native Client 的時機](../../relational-databases/native-client/when-to-use-sql-server-native-client.md)  
 討論 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 在 Microsoft 資料存取技術中扮演什麼角色、它與 Windows DAC 和 ADO.NET 的比較，並提供指標以決定要使用什麼資料存取技術。  
  
 [SQL Server Native Client 功能](../../relational-databases/native-client/features/sql-server-native-client-features.md)  
 描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 所支援的功能。  
  
 [使用 SQL Server Native Client 建立應用程式](../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
 提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 開發的概觀，包括與 Windows DAC 的差異、所使用的元件，以及如何搭配 ADO 使用。  
  
 本章節也會討論 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 安裝和部署，包括如何轉散發 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 程式庫。  
  
 [SQL Server Native Client 的系統需求](../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md)  
 討論使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 所需的系統資源。  
  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
 提供使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者的相關資訊。  
  
 [SQL Server Native Client & #40; ODBC & #41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
 提供使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式的相關資訊。  
  
 [尋找其他 SQL Server Native Client 資訊](../../relational-databases/native-client/finding-more-sql-server-native-client-information.md)  
 提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 的其他相關資源，包括外部資源及取得進一步協助的連結。  
  
 [SQL Server Native Client 錯誤](http://msdn.microsoft.com/library/ebd0e9a8-5fe5-4b15-9a44-2f131a13c186)  
 包含與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 相關聯的執行階段錯誤主題。  
  
## <a name="see-also"></a>另請參閱  
 [從 SQL Server 2005 Native Client 將應用程式更新](../../relational-databases/native-client/applications/updating-an-application-from-sql-server-2005-native-client.md)   
 [ODBC 使用說明主題](../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)   
 [OLE DB 的使用說明主題](../../relational-databases/native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
