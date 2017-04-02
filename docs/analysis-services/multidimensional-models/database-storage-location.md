---
title: "資料庫儲存位置 | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "資料庫 [Analysis Services], 儲存位置"
ms.assetid: cf88c62e-581e-42f2-846f-a9bf1d7c3292
caps.latest.revision: 18
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 18
---
# 資料庫儲存位置
  通常在很多情況下，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫管理員 (dba) 會想要讓特定資料庫放置於伺服器資料夾外部。 這些情況通常是由商務需求所驅使，例如改善效能或展開儲存體。 在這些情況下，**DbStorageLocation** 資料庫屬性可讓 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dba 在本機磁碟或網路裝置中指定資料庫位置。  
  
## DbStorageLocation 資料庫屬性  
 **DbStorageLocation** 資料庫屬性會指定 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 用以建立和管理所有資料庫資料和中繼資料檔案的資料夾。 所有中繼資料檔案都會儲存在 **DbStorageLocation** 資料夾，但資料庫中繼資料檔案除外，因為這種檔案會儲存在伺服器資料夾中。 在設定 **DbStorageLocation** 資料庫屬性的值時有兩個重要的考量：  
  
-   **DbStorageLocation** 資料庫屬性必須設定為現有的 UNC 資料夾路徑或空字串。 空字串是伺服器資料夾的預設值。 如果這個資料夾不存在，當您執行 [建立]、[附加] 或 [改變] 命令時，就會引發錯誤。  
  
-   此外，**DbStorageLocation** 資料庫屬性無法設定為指向伺服器資料夾或其中任何一個子資料夾。 如果此位置指向伺服器資料夾或其中任何一個子資料夾，當您執行 [建立]、[附加] 或 [改變] 命令時，就會引發錯誤。  
  
> [!IMPORTANT]  
>  建議您將 UNC 路徑設定為使用存放區域網路 (SAN)、iSCSI 架構網路或附加於本機的磁碟。 任何網路共用的 UNC 路徑或任何高度延遲的遠端存放區方案，都會導致發生不支援的安裝。  
  
### DbStorageLocation 與 StorageLocation 的比較  
 **DbStorageLocation** 會指定所有資料庫資料和中繼資料檔案所在的資料夾，而 **StorageLocation** 則會指定一或多個 Cube 資料分割所在的資料夾。 **StorageLocation** 可獨立於 **DbStorageLocation** 之外設定。 這是根據預期結果的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dba 決策，而且這兩個屬性的使用方式將多次重疊。  
  
## DbStorageLocation 使用方式  
 在 [卸離]/[連接] 資料庫命令序列、[備份]/[還原] 資料庫命令序列或 [同步] 資料庫命令中，**DbStorageLocation** 資料庫屬性會當作 [建立] 資料庫命令的一部分使用。 變更 **DbStorageLocation** 資料庫屬性會被視為資料庫物件中的結構性變更。 這表示，您必須重新建立所有中繼資料並重新處理資料。  
  
> [!IMPORTANT]  
>  您不應該使用 [改變] 命令來變更資料庫儲存位置。 我們反而建議您使用一序列的 [卸離]/[附加] 資料庫命令 (請參閱 [移動 Analysis Services 資料庫](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)、[附加和卸離 Analysis Services 資料庫](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md))。  
  
## 請參閱＜  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [附加和卸離 Analysis Services 資料庫](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [移動 Analysis Services 資料庫](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [DbStorageLocation 元素](../../analysis-services/xmla/xml-elements-properties/dbstoragelocation-element.md)   
 [Create 元素 &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)   
 [Attach 元素](../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [Synchronize 元素 &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)  
  
  