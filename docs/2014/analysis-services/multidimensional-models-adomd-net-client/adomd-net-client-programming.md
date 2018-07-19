---
title: ADOMD.NET 用戶端程式設計 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- programming [ADOMD.NET]
- ADOMD.NET, programming
ms.assetid: 55156115-ecd1-4ed9-876e-23406af9bbf9
caps.latest.revision: 41
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dd4884abb345f1254c3987acb06e83ced7bcf392
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332748"
---
# <a name="adomdnet-client-programming"></a>ADOMD.NET 用戶端程式設計
  ADOMD.NET 用戶端元件位在 `Microsoft.AnalysisServices.AdomdClient` 命名空間中 (在 microsoft.analysisservices.adomdclient.dll 中)。 這些用戶端元件可提供用戶端的功能和中介層應用程式輕鬆地查詢資料和中繼資料從分析資料存放區，例如[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。  
  
## <a name="using-the-adomdnet-client-objects"></a>了解 ADOMD.NET 用戶端物件  
 在查詢分析資料來源時，需要執行一組一般工作。 下表說明使用 ADOMD.NET 用戶端物件執行這類查詢的一般工作。  
  
|工作|描述|  
|----------|-----------------|  
|[在 ADOMD.NET 中建立連接](connections-in-adomd-net.md)|在 ADOMD.NET 中，您使用 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> 物件建立與分析資料來源之間的連接，例如 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫。 您可以使用 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> 物件來執行命令、擷取資料以及從分析資料來源擷取中繼資料。|  
|[從分析資料來源擷取中繼資料](retrieving-metadata-from-an-analytical-data-source.md)|在建立連接之後，您可以使用各種廣泛的物件擷取有關基礎資料來源的資訊。 這個功能可讓應用程式適應它們已連接的資料來源。|  
|[針對分析資料來源執行命令](executing-commands-against-an-analytical-data-source.md)|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> 物件針對基礎分析資料來源執行命令提供所需的介面。|  
|[從分析資料來源擷取資料](retrieving-data-from-an-analytical-data-source.md)|在執行命令之後，可以使用 <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 或 `System.XmlReader` 物件擷取和剖析資料。|  
|[在 ADOMD.NET 中執行交易](../../relational-databases/native-client-ole-db-transactions/transactions.md)|所有列在這個資料表上一列中的動作，都可能在讀取認可交易中發生，在這個交易中，會在讀取資料時保持共用鎖定，以避免中途讀取 (Dirty Read)。 資料仍然可以在交易結束之前變更，不過這將造成不可重複的讀取或是虛設項目資料。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> 物件提供 ADOMD.NET 中的交易功能。|  
  
 與 ADOMD.NET 物件階層互動通常是從最頂層中的一或多個物件開始，如下表所述。  
  
|若要|使用此物件|  
|--------|---------------------|  
|連接到分析資料來源|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection><br /> <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> 物件代表資料來源連接與資料來源中繼資料。 例如，您可以連接到[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]本機 cube (.cub) 檔案，然後再檢查<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Cubes%2A>屬性，以取得有關出現在分析資料來源上 cube 的中繼資料。 這個物件也代表 `IDbConnection` 介面的實作，這是所有 .NET Framework 資料提供者所需的介面。|  
|探索資料來源的資料採礦功能|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection><br /> <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> 物件會公開數個採礦集合：<br /><br /> -<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection>包含資料來源中每個採礦模型的清單。<br />-<xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection>提供可用之採礦演算法的相關資訊。<br />-<xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection>公開伺服器上採礦結構的相關資訊。|  
|查詢資料來源|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand><br /> <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> 物件代表將傳送到伺服器的陳述式或查詢。 建立資料來源的連接之後，請使用 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> 物件，以支援的語言執行陳述式，例如多維度運算式 (MDX) 或是資料採礦延伸模組 (DMX)。 您也可以使用 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> 物件傳回 <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> 或 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 物件形式的結果。|  
|以快速、有效率的方式擷取資料|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader><br /> 若要建立 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>，可以呼叫 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> 物件的 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> 或 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> 方法。 這個物件會從 .NET Framework 類別庫的 `IDbDataReader` 命名空間實作 `System.Data` 介面。|  
|使用最大量的中繼資料來擷取分析資料|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet><br /> 若要建立 <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>，可以呼叫 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> 的 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A> 或 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> 方法。 在 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> 傳回 <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> 之後，您可以檢查 <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> 所包含的分析資料。|  
|擷取有關 Cube 的中繼資料，例如可用的維度、量值、命名集等等。|<xref:Microsoft.AnalysisServices.AdomdClient.CubeDef><br /> <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> 代表有關 Cube 的中繼資料。 您無法從 <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> 參考 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>。|  
|使用 `System.Data.IDbDataAdapter` 介面擷取資料|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter><br /> <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter> 為現有的 .NET Framework 用戶端應用程式提供唯讀支援。|  
  
## <a name="see-also"></a>另請參閱  
 [ADOMD.NET 伺服器程式設計](../multidimensional-models-adomd-net-server/adomd-net-server-programming.md)   
 [使用 ADOMD.NET 來開發](../multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
  
