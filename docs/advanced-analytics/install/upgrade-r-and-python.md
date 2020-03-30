---
title: 升級 R 與 Python 元件
description: 使用 sqlbindr.exe 升級 SQL Server 機器學習服務或 SQL Server R Services 中的 R 和 Python 以繫結至 Machine Learning Server。
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: abc14f78a969abd4adbbb2dcf12b4ee316614d23
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "69634554"
---
# <a name="upgrade-machine-learning-r-and-python-components-in-sql-server-instances"></a>升級 SQL Server 執行個體中的機器學習 (R 和 Python) 元件
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 中的 R 和 Python 整合包含開放原始碼和 Microsoft 專屬的套件。 在標準 SQL Server 服務下，將根據 SQL Server 發行週期更新套件，並針對目前版本的現有套件進行 Bug 修正，但沒有主要版本升級。 

不過，許多資料科學家都習慣在較新的套件提供使用時使用它們。 針對 SQL Server 機器學習服務 (資料庫內) 和 SQL Server R Services (資料庫內)，您可以透過繫結  至 **Microsoft Machine Learning Server**，取得[較新版本的 R 和 Python](#version-map)。 

## <a name="what-is-binding"></a>何謂繫結？

繫結是一種安裝程序，它會使用來自 [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index) 的較新的可執行檔，程式庫和工具，交換 R_SERVICES 和 PYTHON_SERVICES 資料夾的內容。

隨著更新的元件，服務模型也隨之改變。 使用 [SQL Server 累積更新](https://support.microsoft.com/help/4047329/sql-server-2017-build-versions)，您的服務更新現在符合[現代化生命週期](https://support.microsoft.com/help/30881/modern-lifecycle-policy) (而不是 [SQL Server 產品生命週期](https://support.microsoft.com/lifecycle/search?alpha=SQL%20Server%202017)) 上的 [Microsoft R Server 和 Machine Learning Server 支援時間表](https://docs.microsoft.com/machine-learning-server/resources-servicing-support) \(英文\)。

除了元件版本和服務更新以外，繫結不會變更安裝的基礎：R 和 Python 整合仍然是資料庫引擎執行個體的一部分，授權不變 (沒有與繫結相關的額外成本)，而且 SQL Server 支援原則仍然適用於資料庫引擎。 本文的其餘部分將說明繫結機制，以及它針對每個版本的 SQL Server 的運作方式。

> [!NOTE]
> 繫結僅適用於繫結至 SQL Server 執行個體的 (資料庫內) 執行個體。 繫結與 (獨立式) 安裝無關。

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
**SQL Server 2017 繫結考量**

針對 SQL Server 機器學習服務，只有當 Microsoft Machine Learning Server 開始提供其他套件或現有內容的新版本時，才會考慮繫結。
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
**SQL Server 2016 繫結考量**

針對 SQL Server 2016 R Services 客戶，繫結提供更新的 R套件、不屬於原始安裝的新套件 ([MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) \(英文\)) 和[預先定型模型](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) \(英文\)，這些全都可在 [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index) \(英文\) 每個新的主要和次要版本進一步重新整理。 繫結不會提供 Python 支援，這是 SQL Server 2017 的功能。
::: moniker-end

<a name="version-map"></a>

## <a name="version-map"></a>版本對應

下表是版本對應，顯示了跨發行工具的套件版本，以便在繫結至 Microsoft Machine Learning Server (先前稱為 R Server，從 MLS 9.2.1 開始加入 Python 支援之前) 時，可以確定可能的升級路徑。 

請注意，繫結不保證 R 或 Anaconda 的最新版本。 當您繫結至 Microsoft Machine Learning Server (MLS) 時，您可以透過安裝程式安裝 R 或 Python 版本，安裝程式可能不是 Web 上可用的最新版本。

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
[**SQL Server 2016 R Services**](../install/sql-r-services-windows-install.md)

元件 |初始版本 | [R Server 9.0.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [MLS 9.2.1](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) | [MLS 9.3](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) |
----------|----------------|----------------|--------------|---------|-------|
Microsoft R Open (MRO) (R) | R 3.2.2     | R 3.3.2   |R 3.3.3   | R 3.4.1  | R 3.4.3 |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | 8.0.3  | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)| n.a. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[預先定型的模型](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)| n.a. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| n.a. | 1.0 |  1.0 |  1.0 |  1.0 |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | n.a. | 1.0 |  1.0 |  1.0 |  1.0 |
::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
[**SQL Server 機器學習服務**](../install/sql-machine-learning-services-windows-install.md)

元件 |初始版本 | MLS 9.3 | | | |
----------|----------------|---------|-|-|-|-|
Microsoft R Open (MRO) (R) | R 3.3.3 | R 3.4.3 | | | |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) |   9.2 |  9.3 | | | |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| 1.0 |  1.0 | | | |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 1.0 |  1.0 | | | |
Anaconda 4.2 (Python 3.5)  | 4.2/3.5.2 | 4.2/3.5.2 | | | |
[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2  | 9.3| | | |
[microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[預先定型的模型](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) | 9.2 | 9.3| | | |
::: moniker-end

## <a name="how-component-upgrade-works"></a>元件升級的運作方式 

當您將現有的 R 和 Python 安裝繫結至 Machine Learning Server 時，R 和 Python 程式庫和可執行檔會進行升級。 當您在具有 R 或 Python 整合的現有 SQL Server 資料庫引擎執行個體上執行安裝程式時，[Microsoft Machine Learning Server 安裝程式](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) \(英文\) 會執行繫結。 安裝程式會偵測現有的功能，並提示您重新繫結至 Machine Learning Server。 

在繫結期間，`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES` 和 `\PYTHON_SERVICES` 的內容會被 `C:\Program Files\Microsoft\ML Server\R_SERVER` 和 `\PYTHON_SERVER` 的較新的可執行檔和程式庫覆寫。

同時，服務模型也會從 SQL Server 更新機制轉變為 Microsoft Machine Learning Server 的較頻繁的主要和次要發行週期。 對於需要新一代 R 和 Python 模組作為其解決方案的資料科學小組而言，切換支援原則是個不錯的選項。 

+ 如果沒有繫結，則當您安裝 SQL Server Service Pack 或累積更新 (CU) 時，R 和 Python 套件會針對 Bug 修正進行修補。 
+ 使用繫結，可以根據[現代化生命週期原則](https://support.microsoft.com/help/30881/modern-lifecycle-policy)和Microsoft Machine Learning Server 發行版，獨立於 CU 發行排程之外，將較新的套件版本套用於您的執行個體。 現代化生命週期支援原則在較短的一年生命週期內提供更頻繁的更新。 繫結之後，您將繼續使用 MLS 安裝程式來進行 R 和 Python 的日後更新，因為它們可在 Microsoft 下載網站上取得。

繫結僅適用於 R 和 Python 功能。 也就是適用於 R 和 Python 功能的開放原始碼套件 (Microsoft R Open、Anaconda) 以及專屬套件 RevoScaleR、revoscalepy 等。 繫結不會變更資料庫引擎執行個體的支援模型，也不會變更 SQL Server 的版本。

繫結是可還原的。 您可以藉由[解除繫結執行個體](#bkmk_Unbind)並修復 SQL Server 資料庫引擎執行個體來還原為 SQL Server 服務。

綜上所述，繫結步驟如下：

+ 從現有的，已設定的 SQL Server R Services 或 SQL Server Machine Learning Services 安裝開始。
+ 確定哪個版本的 Microsoft Machine Learning Server 有您想要使用的升級元件。
+ 下載並執行該版本的安裝程式。 安裝程式會偵測現有的執行個體、新增繫結選項，然後傳回相容的執行個體清單。
+ 選擇您想要繫結的執行個體，然後完成安裝程式以執行繫結。

就使用者經驗而言，技術及其使用方式不變。 唯一的差別在於是否有較新版本的套件，以及可能原本無法透過 SQL Server 取得的其他套件。

## <a name="bind-to-mls-using-setup"></a><a name="bkmk_BindWizard"></a>使用安裝程式繫結至 MLS

Microsoft Machine Learning 安裝程式會偵測現有的功能和 SQL Server 版本，並叫用名為 SqlBindR.exe 的公用程式來變更繫結。 就內部而言，SqlBindR 會鏈結至安裝程式並間接使用。 之後，您可以直接從命令列呼叫 SqlBindR，以執行特定的選項。

1. 在 SSMS 中，執行 `SELECT @@version` 以確認伺服器符合最低組建需求。 

   針對 SQL Server 2016 R Services，最低為 [Service Pack 1](https://www.microsoft.com/download/details.aspx?id=54276) 和 [CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1)。

1. 檢查 R base 和 RevoScaleR 套件的版本，確認現有的版本低於您打算用來取代它們的版本。 

    ```sql
    EXECUTE sp_execute_external_script
    @language=N'R'
    ,@script = N'str(OutputDataSet);
    packagematrix <- installed.packages();
    Name <- packagematrix[,1];
    Version <- packagematrix[,3];
    OutputDataSet <- data.frame(Name, Version);'
    , @input_data_1 = N''
    WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
    ```

1. 關閉 SSMS 和與 SQL Server 保持開放連線的任何其他工具。 繫結會覆寫程式檔案。 如果 SQL Server 有已開啟的工作階段，繫結將會失敗，並顯示繫結錯誤碼 6。

1. 將 Microsoft Machine Learning Server 下載到您要升級執行個體的電腦上。 我們建議使用[最新版本](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer) \(英文\)。

1. 將資料夾解壓縮並啟動位於 MLSWIN93 之下的 ServerSetup.exe。

   ![Microsoft Machine Learning Server 安裝精靈](media/mls-921-installer-start.PNG)

1. 在 [設定安裝]  上，確認要升級的元件，並檢閱相容執行個體的清單。 

   這個步驟非常重要。

   在左側，選擇您想要保留或升級的每項功能。 您無法升級某些功能，而不是其他功能。 空白的核取方塊會移除該功能 (假設目前已安裝)。 在螢幕擷取畫面中，指定了 SQL Server 2016 R Services (MSSQL13)、R 和 R 版本的預先定型模型的執行個體。 此設定有效，因為 SQL Server 2016 支援 R，但不支援 Python。

   如果您要升級 SQL Server 2016 R Services 上的元件，請勿選取 [Python] 功能。 您無法將 Python 新增至 SQL Server 2016 R Services。

   在右側，選取執行個體名稱旁邊的核取方塊。 如果未列出任何執行個體，則表示您的組合不相容。 如果您未選取執行個體，則會建立 Machine Learning Server 的新獨立安裝，而 SQL Server 程式庫則不會變更。 如果您無法選取執行個體，則該執行個體可能不在 [SP1 CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1)。 

    ![設定安裝步驟](media/mls-931-installer-mssql13.png)

1. 在 [授權合約]  頁面上，選取 [我接受這些條款]  以接受 Machine Learning Server 的授權條款。 

1. 在後續頁面上，同意您所選取的任何開放原始碼元件 (例如 Microsoft R Open 或 Python Anaconda 散發) 的其他授權條件。

1. 在 [就快完成了]  頁面上，記下安裝資料夾。 預設資料夾為 \Program Files\Microsoft\ML Server。

    如果您想要變更安裝資料夾，請按一下 [進階]  返回精靈的第一頁。 不過，您必須重複所有先前的選取項目。

在安裝程序中，將取代 SQL Server 使用的任何 R 或 Python 程式庫，並更新啟動控制板以使用較新的元件。 因此，如果執行個體先前使用預設 R_SERVICES 資料夾中的程式庫，則升級之後，這些程式庫將被移除，並且啟動控制板服務的屬性已變更為使用新位置中的程式庫。

繫結會影響這些資料夾的內容：C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library 會取代為 C:\Program Files\Microsoft\ML Server\R_SERVER 的內容。 第二個資料夾和其內容是由 Microsoft Machine Learning Server 安裝程式所建立。 

如果升級失敗，請檢查 [SqlBindR 錯誤碼](#sqlbindr-error-codes) 以取得詳細資訊。

## <a name="confirm-binding"></a>確認繫結

重新檢查 R 和 RevoScaleR 的版本，確認您有較新的版本。 使用與資料庫引擎執行個體中的 R 套件一起散發的 R 主控台來取得套件資訊：

```sql
EXECUTE sp_execute_external_script
@language=N'R'
,@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
Name <- packagematrix[,1];
Version <- packagematrix[,3];
OutputDataSet <- data.frame(Name, Version);'
, @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

針對繫結至 Machine Learning Server 9.3 的 SQL Server 2016 R Services，R 基底套件應為 3.4.3，RevoScaleR 應為 9.3，而且您也應該具有 MicrosoftML 9.3。 

如果您已新增預先定型的模型，模型就會內嵌在 MicrosoftML 程式庫中，而您可以透過 MicrosoftML 函式來呼叫它們。 如需詳細資訊，請參閱[適用於 MicrosoftML 的 R 範例](https://docs.microsoft.com/machine-learning-server/r/sample-microsoftml)。

## <a name="offline-binding-no-internet-access"></a>離線繫結 (無法存取網際網路)

對於沒有網際網路連線的系統，您可以將安裝程式和 .cab 檔案下載到連線到網際網路的電腦，然後將檔案傳輸到隔離的伺服器。 

安裝程式 (ServerSetup.exe) 包含 Microsoft 套件 (RevoScaleR、MicrosoftML、olapR、sqlRUtils)。 .cab 檔案提供其他核心元件。 例如，"SRO" cab 提供 R Open，這是 Microsoft 的開放原始碼 R 散發。

下列指示說明如何放置檔案以進行離線安裝。

1. 下載 MLS 安裝程式。 它會以單一壓縮檔案的形式下載。 我們建議您使用[最新版本](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer)，但是您也可以安裝[舊版](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components)。

1. 下載 .cab 檔案。 下列連結適用於 9.3 版本。 如果您需要舊版，可以在 [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components) 中找到其他連結。 回想一下，您只能將 Python/Anaconda 新增至 SQL Server 機器學習服務執行個體。 R 和 Python 都存在預先定型模型；.cab 會以您所使用的語言提供模型。

    | 功能 | 下載 |
    |---------|----------|
    | R       | [SRO_3.4.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=867186&clcid=1033) |
    | Python  | [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054) | 
    | 預先定型的模型 | [MLM_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859053) |

1. 將 .zip 和 .cab 檔案傳送到目標伺服器。

1. 在伺服器上，於 [執行] 命令中輸入 `%temp%`，以取得暫存目錄的實體位置。 實體路徑因機器而異，但通常是 `C:\Users\<your-user-name>\AppData\Local\Temp`。

1. 將 .cab 檔案放在 %temp% 資料夾中。

1. 解壓縮安裝程式。

1. 執行 ServerSetup.exe 並遵循螢幕上的提示來完成安裝。

## <a name="command-line-operations"></a><a name="bkmk_BindCmd"></a>命令列作業

執行 Microsoft Machine Learning Server 之後，就可以使用稱為 SqlBindR.exe 的命令列公用程式，供您用於進一步的繫結作業。 例如，如果您決定解除繫結，則可以重新執行安裝程式或使用命令列公用程式。 此外，您可以使用此工具來檢查執行個體相容性和可用性。

> [!TIP]
> 找不到 SqlBindR 嗎？ 您可能未執行安裝程式。 只有在執行 Machine Learning Server 安裝程式之後，才能使用 SqlBindR。

1. 以系統管理員身分開啟命令提示字元，並瀏覽至包含 sqlbindr.exe 的資料夾。 預設位置是 C:\Program Files\Microsoft\MLServer\Setup

2. 輸入下列命令以檢視可用的執行個體清單︰ `SqlBindR.exe /list`
  
   請記下列出的完整執行個體名稱。 例如，針對預設執行個體，執行個體名稱可能是 MSSQL14.MSSQLSERVER，或類似 SERVERNAME.MYNAMEDINSTANCE 的名稱。

3. 使用 */bind* 引數執行 **SqlBindR.exe** 命令，並使用上一個步驟中所傳回的執行個體名稱指定要升級的執行個體名稱。

   例如，若要升級預設執行個體，請輸入：`SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. 當升級完成後，請重新啟動與任何已修改的執行個體相關的啟動控制板服務。

## <a name="revert-or-unbind-an-instance"></a><a name="bkmk_Unbind"></a>還原或解除繫結執行個體

您可以將繫結的執行個體還原到 R 和 Python 元件的初始安裝 (由 SQL Server 安裝程式建立)。 還原回 SQL Server 服務的過程分為三個部分。

+ [步驟 1：從 Microsoft Machine Learning Server 解除繫結](#step-1-unbind)
+ [步驟 2：將執行個體還原為原始狀態](#step-2-restore)
+ [步驟 3：重新安裝您新增至安裝的任何套件](#step-3-reinstall-packages)

<a name="step-1-unbind"></a> 

### <a name="step-1-unbind"></a>步驟 1:解除繫結

您有兩個復原繫結的選項：重新執行安裝程式，或使用 SqlBindR 命令列公用程式。

#### <a name="unbind-using-setup"></a><a name="bkmk_wizunbind"></a> 使用安裝程式解除繫結

1. 找出 Machine Learning Server 的安裝程式。 如果您已移除安裝程式，則可能需要再次下載，或從另一部電腦複製它。
2. 請務必在具有要解除繫結之執行個體的電腦上執行安裝程式。
2. 安裝程式會識別用於解除繫結之候選項目的本機執行個體。
3. 取消選取您想要還原為原始設定之執行個體旁的核取方塊。
4. 接受授權合約。 即使在安裝時，您也必須表示您接受授權條款。
5. 按一下 [完成]  。 該程序需要一段時間。

#### <a name="unbind-using-the-command-line"></a><a name="bkmk_cmdunbind"></a> 使用命令列解除繫結

1. 開啟命令提示字元並瀏覽至包含 **sqlbindr.exe** 的資料夾，如上一節所述。

2. 搭配 */unbind* 引數執行 **SqlBindR.exe** 命令，並指定執行個體。

   例如，以下命令列會還原預設執行個體：
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

<a name="step-2-restore"></a> 

###  <a name="step-2-repair-the-sql-server-instance"></a>步驟 2:修復 SQL Server 執行個體

執行 SQL Server 安裝程式，以修復具有 R 和 Python 功能的資料庫引擎執行個體。 系統會保留現有的更新，但如果您遺漏 R 和 Python 套件的任何 SQL Server 服務更新，則此步驟會套用這些修補程式。

或者，這需要更多的工作，但是您也可以完全解除安裝並重新安裝資料庫引擎執行個體，然後套用所有服務更新。

<a name="step-3-reinstall-packages"></a> 

### <a name="step-3-add-any-third-party-packages"></a>步驟 3：新增任何協力廠商套件

您可能已將其他開放原始碼或協力廠商套件新增至您的套件程式庫。 由於反轉繫結會切換預設封裝程式庫的位置，因此必須將套件重新安裝至 R 和 Python 現在使用的程式庫中。 如需詳細資訊，請參閱 [R 套件資訊](../package-management/r-package-information.md)和[安裝](../package-management/install-additional-r-packages-on-sql-server.md)，以及 [Python 套件資訊](../package-management/python-package-information.md)和[安裝](../package-management/install-additional-python-packages-on-sql-server.md)。

## <a name="sqlbindrexe-command-syntax"></a>SqlBindR.exe 命令語法

### <a name="usage"></a>使用量

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>參數

|名稱|描述|
|------|------|
|list | 顯示目前電腦上所有 SQL 資料庫執行個體識別碼的清單|
|*bind*| 將指定的 SQL 資料庫執行個體升級到最新版 R Server，並確保執行個體自動取得 R Server 的未來升級|
|*unbind*|從指定的 SQL 資料庫執行個體解除安裝最新版的 R Server，並防止未來的 R Server 升級影響執行個體|

<a name="sqlbindr-error-codes"><a/>

## <a name="binding-errors"></a>繫結錯誤

MLS 安裝程式和 SqlBindR 都會傳回下列錯誤碼和訊息。

|錯誤碼  | 訊息           | 詳細資料               |
|------------|-------------------|-----------------------|
|繫結錯誤 0 | 確定 (成功) | 已傳遞繫結，但沒有任何錯誤。 |
|繫結錯誤 1 | 無效的引數 | 語法錯誤。 |
|繫結錯誤 2 | 無效的動作 | 語法錯誤。 |
|繫結錯誤 3 | 無效的執行個體 | 執行個體存在，但對繫結無效。 |
|繫結錯誤 4 | 不可繫結 | |
|繫結錯誤 5 | 已繫結 | 您執行了 *bind* 命令，但指定的執行個體已經繫結。 |
|繫結錯誤 6 | 繫結失敗 | 解除繫結執行個體時發生錯誤。 如果您執行 MLS 安裝程式，但未選取任何功能，就會發生此錯誤。 繫結需要您同時選取 MSSQL 執行個體與 R 和 Python (假設執行個體是 SQL Server 2017)。 如果 SqlBindR 無法寫入 Program Files 資料夾，也會發生此錯誤。 開啟工作階段或 SQL Server 的控制代碼會導致此錯誤發生。 如果您收到此錯誤，請在啟動任何新的工作階段之前，將電腦重新開機並重做繫結步驟。|
|繫結錯誤 7 | 未繫結 | 資料庫引擎執行個體具有 R Services 或 SQL Server 機器學習服務。 執行個體未繫結至 Microsoft Machine Learning Server。 |
|繫結錯誤 8 | 解除繫結失敗 | 解除繫結執行個體時發生錯誤。 |
|繫結錯誤 9 | 找不到任何執行個體 | 在這部電腦上找不到任何資料庫引擎執行個體。 |

## <a name="known-issues"></a>已知問題

本節列出使用 SqlBindR.exe 公用程式的特定已知問題，或可能會影響 SQL Server 執行個體之 Machine Learning Server 升級的已知問題。

### <a name="restoring-packages-that-were-previously-installed"></a>還原先前安裝的套件

如果您升級至 Microsoft R Server 9.0.1，則該版本的 SqlBindR.exe 版本無法完全還原原始套件或 R 元件，要求使用者在執行個體上執行 SQL Server 修復、套用所有服務版本，然後重新啟動執行個體。

較新版本的 SqlBindR 會自動還原 R 原始功能，而不需要重新安裝 R 元件或重新修補伺服器。 不過，您必須安裝在初始安裝之後可能已新增的任何 R 套件更新。

如果您已使用套件管理角色來安裝和共用套件，則此工作會變得更容易：您可以使用 R 命令使用資料庫中的記錄將已安裝的套件同步處理到檔案系統，反之亦然。 如需詳細資訊，請參閱 [SQL Server 的 R 套件管理](../r/install-additional-r-packages-on-sql-server.md)。

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>從 SQL Server 進行多重升級的問題

如果您先前已將 SQL Server 2016 R Services 的執行個體升級至 9.0.1，當您執行 Microsoft R Server 9.1.0 的新安裝程式時，它會顯示所有有效執行個體的清單，然後依預設選取先前繫結的執行個體。 如果繼續，先前繫結的執行個體會解除繫結。 如此一來，就會移除先前的 9.0.1 安裝，包括任何相關的套件，但不會安裝新版的 Microsoft R Server (9.1.0)。

因應措施是修改現有的 R Server 安裝，如下所示：
1. 在 [控制台] 中，開啟 [新增或移除程式]  。
2. 找出 Microsoft R Server，然後按一下 [變更/修改]  。
3. 當安裝程式啟動時，請選取您想要繫結至 9.1.0 的執行個體。

Microsoft Machine Learning Server 9.2.1 和 9.3 不會有這個問題。

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>繫結或解除繫結會保留多個暫存資料夾

有時繫結或解除繫結作業無法清除暫存資料夾。
如果您找到名稱類似的資料夾，您可以在安裝完成後將其移除：R_SERVICES_<guid>

> [!NOTE]
> 請務必等到安裝完成。 移除與某個版本相關聯的 R 程式庫，然後再加入新的 R 程式庫可能需要很長時間。 當作業完成時，就會移除暫存資料夾。

## <a name="see-also"></a>另請參閱

+ [安裝適用於 Windows 的 Machine Learning Server (已連線到網際網路)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [安裝適用於 Windows 的 Machine Learning Server (離線)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)
+ [Machine Learning Server 中的已知問題](https://docs.microsoft.com/machine-learning-server/resources-known-issues)
+ [舊版 R Server 的功能公告](https://docs.microsoft.com/r-server/whats-new-in-r-server)
+ [已淘汰、已停止或已變更的功能](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)
