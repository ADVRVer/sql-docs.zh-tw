---
title: 建立本機封裝儲存機制使用 miniCRAN |Microsoft 文件
titleSuffix: SQL Server
ms.custom: ''
ms.date: 02/20/2018
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: 6dfaa01607bb25e1afe41301e655025a8d2b059f
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/04/2018
---
# <a name="create-a-local-package-repository-using-minicran"></a>建立使用 miniCRAN 本機封裝儲存機制
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[MiniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) Andre de Vries 來支援這些一般的案例建立封裝： 

+ 分析單一封裝或個封裝的封裝相依性
+ 準備安裝到沒有網際網路存取的伺服器上的一組 R 封裝。

使用者指定一組所需的封裝，並 miniCRAN 遞迴讀取這些封裝的相依性樹狀結構，而且會從 CRAN 或類似的儲存機制下載列出的封裝和其相依性。

做為輸出，miniCRAN 會建立所選的套件和所有必要的相依性所組成的內部一致存放庫。 您可以將這個本機儲存機制移至伺服器，並繼續進行而不使用網際網路安裝封裝。

有經驗的 R 使用者通常會查看針對下載的封裝 DESCRIPTION 檔案中的相依封裝的清單。 不過，封裝會列入**匯入**可能有第二個層級相依性。 基於這個理由，我們建議使用**miniCRAN**方法。

## <a name="what-is-a-package-repository"></a>什麼是封裝儲存機制

建立本機封裝儲存機制的目標是提供伺服器管理員或組織中的其他使用者可用來在沒有網際網路存取的伺服器上安裝新的 R 封裝的單一位置。 建立儲存機制之後, 您可以藉由新增新的封裝，或升級現有的封裝的版本修改它。

[MiniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html)封裝的寫入為 R [Andre de Vries](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html)可更輕鬆地建立一致，受管理的組 R 封裝的組織。 

封裝儲存機制是在這些情況下很有用：

- **安全性**： 許多 R 使用者習慣於下載和安裝新的 R 封裝，在從 CRAN 或其中一個鏡像站台。 不過，基於安全性理由，實際執行伺服器執行[!INCLUDE[ssNoVersion_md](..\..\includes\ssnoversion-md.md)]通常不需要網際網路連線。

- **更容易離線安裝**： 若要封裝安裝到離線的伺服器需要，您也可以下載所有套件相依性，使用 miniCRAN 可讓您更輕鬆地取得正確格式的所有相依性。

    藉由使用 miniCRAN，您可以避免封裝相依性錯誤準備要使用安裝套件時[建立外部程式庫](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)陳述式。

- **版本管理改善**： 在多使用者環境中，有合理的原因，若要避免不受限制的伺服器上的多個封裝版本的安裝。 使用本機儲存機制以提供一致的封裝集以供分析師。 

> [!TIP]
> 您也可以使用 miniCRAN 準備封裝以便在 Azure Machine Learning 中使用。 如需詳細資訊，請參閱這篇部落格： [miniCRAN 使用在 Azure ML，由 Michele Usuelli](https://www.r-bloggers.com/using-minicran-in-azure-ml/) 

## <a name="prepare-packages-using-minicran"></a>準備使用 miniCRAN 封裝

**MiniCRAN**封裝本身會相依於其他 18 CRAN 封裝，也就是之間**RCurl**封裝，有系統相依性上**curl 對內**封裝。 同樣地，封裝**XML**具有相依性**libxml2 對內**。 

基於這些理由，我們建議您建立本機儲存機制一開始包含完整的網際網路存取的電腦上，讓您可以輕鬆地滿足所有這些相依性。 

建立儲存機制之後，您可以移動至不同的位置的儲存機制。

### <a name="step-1-install-the-minicran-package"></a>步驟 1： 安裝 miniCRAN 套件

您開始建立**miniCRAN**要當做來源使用的儲存機制。 您應該可以存取網際網路的電腦上建立這個儲存機制。

1. 安裝**miniCRAN**封裝和所需**igraph**封裝。 這個範例會檢查是否已安裝封裝，但您可以略過 if 陳述式並直接安裝封裝。

    ```R
    if(!require("miniCRAN")) install.packages("miniCRAN") 
    if(!require("igraph")) install.packages("igraph") 
    library("miniCRAN")
    ```

### <a name="step-2-define-a-package-source-a-cran-mirror-or-an-mran-snapshot"></a>步驟 2： 定義封裝來源： CRAN 鏡像或 MRAN 快照集

1. 指定要用於取得封裝的鏡像網站。 例如，您可以使用 MRAN 站台或任何其他站台在您的地區，其中包含您需要的套件。 如果下載失敗，請嘗試另一個鏡像網站。

    ```R
    CRAN_mirror <- c(CRAN = "https://mran.microsoft.com")
    CRAN_mirror <- c(CRAN = "https://cran.cnr.berkeley.edu")
    ```

2. 輸入用來儲存收集的封裝的本機資料夾的名稱。 

    請務必事先建立資料夾。 如果會引發錯誤`local_repo`資料夾不存在，當您稍後執行的 R 程式碼。

    資料夾應該具有描述性的名稱。 這裡我們使用 「 miniCRAN"，但如果您重複此步驟通常，您應該使用更具描述性的名稱，例如"miniCRANZooPackages"或"miniCRANMyRPackagev2"。

    ```R
    local_repo <- "~/miniCRAN"
    ```

    波狀符號展開運算子所傳回的結果相當於的環境變數， `Sys.getenv("R_USER")`。

### <a name="step-3-add-packages-to-the-repository"></a>步驟 3： 將封裝新增至儲存機制

1. 之後**miniCRAN**已安裝，建立指定您想要下載的其他封裝的清單。

    請勿**不**加入這個初始清單中的相依性。 **Igraph**所使用的封裝**miniCRAN**為您產生相依性的清單。 如需如何使用產生的相依性圖形的詳細資訊，請參閱[來識別封裝的相依性使用 miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html)。

    下列的 R 指令碼會新增目標的封裝，"zoo"和 「 預測 」 變數。

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```
2. 它不需要您繪製相依性圖表，但很有幫助。
    
    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. 建立本機儲存機制。 請務必視需要變更的 R 版本

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3");
    ```

    這項資訊，從 miniCRAN 封裝會建立您要複製之封裝的資料夾結構[!INCLUDE[ssNoVersion_md](..\..\includes\ssnoversion-md.md)]更新版本。

4. 此時您應該有包含在需要時，封裝的資料夾和任何其他封裝的所需。

    您可以執行下列程式碼列出 miniCRAN 儲存機制中所包含的封裝。

    ```R
    pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE);
    head(pdb);
    pdb$Package;
    pdb[, c("Package", "Version", "License")]
    ```

### <a name="step-4-use-the-repository-to-add-r-packages-to-the-instance-library"></a>步驟 4： 若要將 R 封裝新增至執行個體文件庫中使用的儲存機制

您已建立儲存機制，並加入您需要的套件之後，您必須將封裝儲存機制移至伺服器電腦，並確保 R 封裝會安裝在正確的程式庫，以用於 SQL Server。

下列程序描述如何安裝封裝使用的 R 工具。

1. 複製包含 miniCRAN 儲存機制，以您要安裝封裝的伺服器，將整個資料夾。 資料夾通常具有此結構： miniCRAN 根目錄 >]-> [bin]-> [windows]-> [contrib 不]-> [版本]-> [所有封裝。

2. 開啟 R 命令提示字元使用執行個體相關聯的 R 工具。

    - 預設資料夾是針對 SQL Server 2017， `C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library`。

    - 就 SQL Server 2016 而言，預設資料夾是 `C:/Program Files/Microsoft SQL Server/MSSQL13.MSSQLSERVER/R_SERVICES/library`。

    - 具名的執行個體，預設路徑看起來應該像： `<instance_path>.RTEST/R_SERVICES/library`。

    -  如果您已將 SQL Server 安裝到不同的磁碟機，或在安裝路徑中進行了任何其他變更，並務必一併進行這些變更。

3. 取得執行個體文件庫的路徑，並將它加入至程式庫路徑的清單。

    ```R
    .libPaths()[1];
    lib <- .libPaths()[1]
    ```

    在 SQL Server，此命令應該會傳回執行個體相關聯，例如程式庫的路徑:"c: / Program 檔案/Microsoft SQL Server/MSSQL14。MSSQLSERVER/R_SERVICES/媒體櫃 」

4. 指定新的位置複製其中的伺服器上**miniCRAN**儲存機制，做為`server_repo`。

    在此範例中，我們假設您在伺服器上的暫存資料夾複製儲存機制。

    ```R
    source_repo <- "C:\\temp\\miniCRAN"
    ```

5. 因為您正在伺服器上新的 R 工作區中，您也必須提供要安裝套件的清單。

    ```R
    tspackages <- c("zoo", "forecast")
    ```

6. 安裝封裝，並提供本機複本 miniCRAN 儲存機制的路徑。

    ```R
    install.packages(tspackages, repos = file.path("file://", normalizePath;(source_repo, winslash = "/")), lib = lib, type = "win.binary", dependencies = TRUE);
    ```

7. 從執行個體文件庫中，您可以檢視已安裝的封裝，使用類似下列的命令：

    ```R
    installed.packages()
    ```

> [!NOTE] 
> 若要使用 SQL Server 中的封裝，封裝必須安裝到預設執行個體所使用的程式庫。 

## <a name="manually-install-a-single-package-from-a-zipped-file"></a>手動安裝在單一封裝 zip 檔案

如果您要安裝的單一封裝沒有相依性，或您不能使用**miniCRAN**，您可以手動下載您需要的套件。 若要這樣做，您都必須是系統管理員或伺服器的唯一擁有者。

下載封裝之後, 您可以安裝的 R 封裝從 zip 的檔案的位置。

1. 下載為 zip 檔案，封裝，並將它儲存在本機資料夾

2. 複製到該資料夾[!INCLUDE[ssNoVersion_md](..\..\includes\ssnoversion-md.md)]電腦。

3. 將封裝安裝到使用傳統的 R 命令 SQL Server 執行個體文件庫。 如果封裝有相依性，尚未安裝，而且不包含這些，安裝可能會失敗。 

您也可以上傳個別封裝的 SQL Server 2017，執行個體使用[建立外部程式庫陳述式](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)。 此程序也需要 「 系統管理存取權。
