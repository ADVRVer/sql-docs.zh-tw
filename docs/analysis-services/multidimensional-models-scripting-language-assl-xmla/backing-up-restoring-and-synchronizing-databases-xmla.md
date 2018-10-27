---
title: 備份、 還原和同步處理資料庫 (XMLA) |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 19d311a07eb11f1c5119a3c20d7536b5a2986b49
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145933"
---
# <a name="backing-up-restoring-and-synchronizing-databases-xmla"></a>備份、還原和同步處理資料庫 (XMLA)
  在 XML for Analysis 中，有三個命令分別可用來備份、還原和同步處理資料庫：  
  
-   [備份](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla)命令會備份[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]備份檔案 (.abf)，一節中所述[備份資料庫](#backing_up_databases)。  
  
-   [還原](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla)命令還原[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]一節中所述，從.abf 檔案，資料庫[還原資料庫](#restoring_databases)。  
  
-   [Synchronize](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla)命令會同步處理某個[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]一節中所述，使用資料和中繼資料的另一個資料庫，資料庫[同步處理資料庫](#synchronizing_databases)。  
  
##  <a name="backing_up_databases"></a> 備份資料庫  
 如稍早所述**備份**命令會指定備份[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]資料庫備份至備份檔案。 **備份**命令具有各種屬性，可讓您指定的資料庫備份，若要使用，如何備份安全性定義，以及要備份的遠端資料分割的備份檔案。  
  
> [!IMPORTANT]  
>  Analysis Services 服務帳戶必須擁有針對每個檔案所指定之備份位置的寫入權限。 此外，使用者必須具有下列其中一個角色： [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的管理員角色，或在要備份之資料庫上擁有「完整控制權 (管理員)」權限的資料庫角色成員。  
  
### <a name="specifying-the-database-and-backup-file"></a>指定資料庫與備份檔案  
 若要指定要備份的資料庫，您設定[物件](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)屬性**備份**命令。 **物件**屬性必須包含的物件識別碼的資料庫，或發生錯誤。  
  
 若要指定的檔案，可供建立及使用的備份程序，您設定[檔案](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/file-element-xmla)屬性**備份**命令。 **檔案**屬性應設為要建立的備份檔案的 UNC 路徑和檔案名稱。  
  
 除了指定用於備份的檔案之外，還可以為指定的備份檔案設定下列選項：  
  
-   如果您設定[AllowOverwrite](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/allowoverwrite-element-xmla)屬性設為 true，**備份**命令覆寫備份的檔案，如果指定的檔案已經存在。 如果您設定**AllowOverwrite**屬性設定為 false，則會發生錯誤如果指定的備份檔案已經存在。  
  
-   如果您設定[ApplyCompression](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/applycompression-element-xmla)屬性設為 true，備份檔案會壓縮檔案建立之後。  
  
-   如果您設定[密碼](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/password-element-xmla)屬性設為任何非空白值時，備份檔案會使用指定的密碼來加密。  
  
    > [!IMPORTANT]  
    >  如果**ApplyCompression**並**密碼**屬性沒有指定，則備份的檔案會以純文字中的連接字串儲存使用者名稱和密碼所包含。 以純文字儲存的資料可能會被擷取。 為了提高安全性，使用**ApplyCompression**並**密碼**設定來壓縮和加密備份檔案。  
  
### <a name="backing-up-security-settings"></a>備份安全性設定  
 [安全性](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/security-element-xmla)屬性會決定是否**備份**命令備份的安全性定義，例如上定義的角色和權限，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]資料庫。 **安全性**屬性也會決定備份檔案包含的 Windows 使用者帳戶和群組定義為安全性定義成員。  
  
 值**安全性**屬性僅限於其中一個下表所列的字串。  
  
|值|描述|  
|-----------|-----------------|  
|*skipMembership*|在備份檔案中納入安全性定義，但是排除成員資格資訊。|  
|*CopyAll*|在備份檔案中納入安全性定義與成員資格資訊。|  
|*IgnoreSecurity*|從備份檔案排除安全性定義。|  
  
### <a name="backing-up-remote-partitions"></a>備份遠端資料分割  
 若要將備份遠端資料分割中[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]資料庫中，設定[BackupRemotePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/backupremotepartitions-element-xmla)屬性**備份**命令設為 true。 此設定會導致**備份**命令來建立每個遠端資料來源用來儲存資料庫的遠端資料分割的遠端備份檔案。  
  
 備份每個遠端資料來源，您可以指定其對應的備份檔案，藉以[位置](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/location-element-xmla)中的項目[位置](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/locations-element-xmla)屬性**備份**命令。 **位置**項目應該有其**檔案**屬性設定為 UNC 路徑和檔案名稱之遠端備份檔案，並將其[DataSourceID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceid-element-xmla)屬性設定為識別項在資料庫中定義的遠端資料來源。  
  
##  <a name="restoring_databases"></a> 還原資料庫  
 **還原**命令會還原指定[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]資料庫從備份檔案。 **還原**命令具有各種屬性，可讓您指定要備份的檔案，若要使用，如何還原安全性定義、 要儲存的遠端資料分割和重新放置還原的資料庫關聯式 OLAP (ROLAP)物件。  
  
> [!IMPORTANT]  
>  對於每個備份檔案，執行還原命令的使用者必須擁有從針對每個檔案所指定之備份位置讀取的權限。 若要還原沒有安裝在伺服器上的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫，使用者也必須是該 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體之伺服器角色的成員。 若要覆寫 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫，使用者必須具有下列其中一個角色：[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體之伺服器角色的成員，或在要還原之資料庫上擁有「完整控制權 (管理員)」權限的資料庫角色成員。  
  
> [!NOTE]  
>  還原現有的資料庫之後，還原資料庫的使用者可能會喪失已還原資料庫的存取權。 如果在執行備份時，使用者不是伺服器角色的成員，也不是擁有完整控制權 (管理員) 權限的資料庫角色成員，就可能會發生存取權喪失的情況。  
  
### <a name="specifying-the-database-and-backup-file"></a>指定資料庫與備份檔案  
 **DatabaseName**屬性**還原**命令必須包含的物件識別碼的資料庫，或發生錯誤。 如果指定的資料庫已經存在， **AllowOverwrite**屬性會決定是否要覆寫現有的資料庫。 如果**AllowOverwrite**屬性設定為 false，而且指定的資料庫已經存在，則會發生錯誤。  
  
 您應該設定**檔案**屬性**還原**命令還原到指定的資料庫備份檔案之 UNC 路徑和檔案名稱。 您也可以設定**密碼**屬性指定的備份檔案。 如果**密碼**屬性設定為任何非空白值時，使用指定的密碼來解密備份檔案。 如果備份檔案未加密，或者如果指定的密碼不符合用以加密備份檔案的密碼，就會發生錯誤。  
  
### <a name="restoring-security-settings"></a>還原安全性設定  
 **安全性**屬性會決定是否**還原**命令會還原安全性定義，例如角色和權限，定義於[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]資料庫。 **安全性**屬性也會決定是否**還原**命令包含的 Windows 使用者帳戶和群組定義為安全性定義成員為還原程序的一部分。  
  
 這個元素的值限制為下表所列的其中一個字串。  
  
|值|描述|  
|-----------|-----------------|  
|*skipMembership*|在資料庫中納入安全性定義，但是排除成員資格資訊。|  
|*CopyAll*|在資料庫中納入安全性定義與成員資格資訊。|  
|*IgnoreSecurity*|從資料庫排除安全性定義。|  
  
### <a name="restoring-remote-partitions"></a>還原遠端資料分割  
 針對每個在前一個期間建立的遠端備份檔案**備份**命令時，您可以藉由還原其相關聯的遠端資料分割**位置**中的項目**位置**的屬性**還原**命令。 [DataSourceType](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourcetype-element-xmla)屬性分別**位置**必須排除項目，或明確設定為*遠端*。  
  
 對於每個指定**位置**項目[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]執行個體會連絡在指定的遠端資料來源**DataSourceID**還原遠端備份檔案中定義的分割區的屬性中指定**檔案**屬性。 除了**DataSourceID**並**檔案**屬性，下列屬性可針對每個**位置**用來還原遠端資料分割的項目：  
  
-   若要覆寫中指定的遠端資料來源的連接字串**DataSourceID**，您可以設定**ConnectionString**屬性**位置**項目不同的連接字串。 **還原**命令接著會使用連接字串中包含**ConnectionString**屬性。 如果**ConnectionString**未指定，則**還原**命令會使用指定的遠端資料來源的備份檔案中儲存的連接字串。 您可以使用**ConnectionString**設定設為 遠端資料分割移到不同的遠端執行個體。 不過，您無法使用**ConnectionString**設定設為相同的執行個體，其中包含已還原的資料庫還原遠端資料分割。 換句話說，您無法使用**ConnectionString**遠端資料分割變成本機資料分割的屬性。  
  
-   每個原始資料夾用來儲存遠端資料來源上的遠端資料分割，您可以指定[資料夾](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/folder-element-xmla)元素，以指定要還原儲存在原始資料夾中的所有遠端資料分割中的新資料夾。 如果**資料夾**項目未指定，**還原**命令會使用指定的遠端備份檔案中包含遠端資料分割的原始資料夾。  
  
### <a name="relocating-rolap-objects"></a>重新放置 ROLAP 物件  
 **還原**命令無法還原彙總或使用 ROLAP 儲存，因為這類資訊會儲存在基礎關聯式資料來源的資料表中的物件資料。 不過，可以還原 ROLAP 物件的中繼資料。 若要還原 ROLAP 物件的中繼資料**還原**命令重新建立關聯式資料來源的資料表結構。  
  
 您可以使用**位置**中的項目**還原**重新放置 ROLAP 物件的命令。 每個**位置**用來重新放置資料來源的項目**DataSourceType**屬性必須明確設定為*本機*。 您也必須設定**ConnectionString**屬性**位置**至新位置的連接字串的項目。 在還原期間，**還原**命令將會取代所識別的資料來源的連接字串**DataSourceID**屬性**位置**項目值是**ConnectionString**屬性**位置**項目。  
  
##  <a name="synchronizing_databases"></a> 同步處理資料庫  
 **Synchronize**命令會同步處理的資料和中繼資料指定[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]與另一個資料庫的資料庫。 **同步處理**命令具有各種屬性，可讓您指定來源資料庫中，如何同步處理安全性定義、 要同步處理，遠端資料分割和 ROLAP 物件的同步處理。  
  
> [!NOTE]  
>  **同步處理**只能由伺服器管理員與資料庫管理員可以執行命令。 來源與目的地資料庫都必須具有相同的資料庫相容性層級。  
  
### <a name="specifying-the-source-database"></a>指定來源資料庫  
 [來源](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)屬性**同步處理**命令中包含兩個屬性**ConnectionString**並**物件**。 **ConnectionString**屬性包含連接字串的執行個體，其中包含來源資料庫，而**物件**屬性包含來源資料庫的物件識別項。  
  
 目的地資料庫的目前資料庫中的工作階段**同步處理**命令會執行。  
  
 如果**ApplyCompression**屬性**同步處理**命令設定為 true，從來源傳送的資訊到目的地資料庫的資料庫會在傳送之前先進行壓縮。  
  
### <a name="synchronizing-security-settings"></a>同步處理安全性設定  
 [SynchronizeSecurity](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/security-element-xmla)屬性會決定是否**同步處理**命令會同步處理安全性定義，例如角色和權限，在來源資料庫上定義。 **SynchronizeSecurity**屬性也會決定是否**還**命令包含的 Windows 使用者帳戶和群組定義為安全性定義成員。  
  
 這個元素的值限制為下表所列的其中一個字串。  
  
|值|描述|  
|-----------|-----------------|  
|*skipMembership*|在目的地資料庫中納入安全性定義，但是排除成員資格資訊。|  
|*CopyAll*|在目的地資料庫中納入安全性定義與成員資格資訊。|  
|*IgnoreSecurity*|從目的地資料庫排除安全性定義。|  
  
### <a name="synchronizing-remote-partitions"></a>同步處理遠端資料分割  
 來源資料庫上存在每個遠端資料來源，您可以同步處理每個相關聯的遠端資料分割包括**位置**中的項目**位置**屬性**同步處理**命令。 每個**位置**項目**DataSourceType**屬性必須排除在外或明確設定為*遠端*。  
  
 定義並連接到目的地資料庫，在遠端資料來源**Synchronize**命令會使用連接字串中定義**ConnectionString**屬性**位置**項目。 **Synchronize**命令接著會使用**DataSourceID**屬性**位置**來識別要同步處理哪些遠端資料分割的項目。 **Synchronize**命令會同步處理遠端資料來源中指定的遠端資料分割**DataSourceID** 中指定遠端資料來源的來源資料庫上的屬性**DataSourceID**目的地資料庫上的屬性。  
  
 每個原始資料夾用來儲存遠端資料分割上來源資料庫上的遠端資料來源，您也可以指定**資料夾**中的項目**位置**項目。 **資料夾**元素表示用來同步處理儲存在遠端資料來源原始資料夾中的所有遠端資料分割的目的地資料庫的新資料夾。 如果**資料夾**項目未指定，Synchronize 命令會使用指定包含來源資料庫中的遠端資料分割的原始資料夾。  
  
### <a name="synchronizing-rolap-objects"></a>同步處理 ROLAP 物件  
 **同步處理**命令無法同步處理，彙總或使用 ROLAP 儲存，因為這類資訊會儲存在基礎關聯式資料來源的資料表中的物件資料。 不過，可以同步處理 ROLAP 物件的中繼資料。 若要同步處理中繼資料中，**同步處理**命令會重新建立關聯式資料來源的資料表結構。  
  
 您可以使用**位置**同步處理 ROLAP 物件的同步處理命令中的項目。 每個**位置**用來重新放置資料來源的項目**DataSourceType**屬性必須明確設定為*本機*。 . 您也必須設定**ConnectionString**屬性**位置**至新位置的連接字串的項目。 同步處理期間， **Synchronize**命令將會取代所識別的資料來源的連接字串**DataSourceID**屬性**位置**值的項目**ConnectionString**屬性**位置**項目。  
  
## <a name="see-also"></a>另請參閱  
 [Backup 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla)   
 [Restore 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla)   
 [Synchronize 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla)   
 [備份與還原 Analysis Services 資料庫](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
