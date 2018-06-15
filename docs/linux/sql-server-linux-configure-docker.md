---
title: SQL Server 2017 docker 設定選項 |Microsoft 文件
description: 瀏覽不同的方式使用，並與其互動在 Docker 中的 SQL Server 2017 容器映像。 這包括複製檔案及疑難排解的保存資料。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/26/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.technology: linux
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
ms.custom: sql-linux
ms.openlocfilehash: aaca3ddf90b6002f259279c5b8f51980f2964996
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
ms.locfileid: "34455631"
---
# <a name="configure-sql-server-2017-container-images-on-docker"></a>設定 SQL Server 2017 容器映像 docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

這篇文章說明如何設定及使用[mssql-伺服器-linux 容器映像](https://hub.docker.com/r/microsoft/mssql-server-linux/)使用 Docker。 此映像包含以 Ubuntu 16.04 為基礎，在 Linux 上執行的 SQL Server。 您可於適用於 Mac/Windows 的 Docker 上將其與 Docker 引擎 1.8 以上版本搭配使用。

> [!NOTE]
> 這篇文章特別著重在使用 mssql-伺服器-linux 映像。 未涵蓋的 Windows 映像，但您可以深入了解上[mssql 伺服器 windows Docker Hub 頁面](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)。

## <a name="pull-and-run-the-container-image"></a>提取及執行容器映像

若要提取，而且執行 SQL Server 2017 Docker 容器映像，請遵循的必要條件和下列快速入門中的步驟：

- [執行 SQL Server 2017 容器映像使用 Docker](quickstart-install-connect-docker.md)

設定本文提供下列各節中的其他使用案例。

## <a id="production"></a> 執行實際執行的容器映像

快速入門中上一節會從 Docker Hub 執行免費的 SQL Server 的開發人員版本。 如果您想要執行實際執行的容器映像，例如 Enterprise、 Standard 或 Web edition，仍適用於大部分的資訊。 不過，有幾項差異，此處所述。

- 如果您有有效的授權，可以只在生產環境中使用 SQL Server。 您可以取得免費的 SQL Server Express 生產授權[這裡](https://go.microsoft.com/fwlink/?linkid=857693)。 SQL Server Standard 和 Enterprise Edition 授權都是透過[Microsoft 大量授權](https://www.microsoft.com/Licensing/licensing-programs/licensing-programs.aspx)。

- 實際執行 SQL Server 容器映像必須取自[Docker 存放區](https://store.docker.com)。 如果您還沒有一個 Docker 存放區上建立帳戶。

- 開發人員的容器映像，Docker 存放區上可以設定為執行的實際執行版本。 若要執行實際執行版本中使用下列步驟：

   1. 首先，您的 docker id 登入，從命令列。

      ```bash
      docker login
      ```

   1. 接著，您必須取得免費的開發人員 Docker 存放區上的容器映像。 移至[https://store.docker.com/images/mssql-server-linux](https://store.docker.com/images/mssql-server-linux)，按一下 **繼續簽出**，並遵循指示。

   1. 檢閱需求，並執行程序[快速入門](quickstart-install-connect-docker.md)。 但是，有兩個差異。 您必須先提取映像**存放區/microsoft/mssql-伺服器-linux:\<標記名稱\>** 從 Docker 存放區。 您必須指定與您生產環境版本**MSSQL_PID**環境變數。 下列範例會示範如何執行 Enterprise edition 的最新的 SQL Server 2017 容器映像：

      ```bash
      docker run --name sqlenterprise \
         -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
         -e 'MSSQL_PID=Enterprise' -p 1433:1433 \
         -d store/microsoft/mssql-server-linux:2017-latest
      ```

      ```PowerShell
      docker run --name sqlenterprise `
         -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
         -e "MSSQL_PID=Enterprise" -p 1433:1433 `
         -d "store/microsoft/mssql-server-linux:2017-latest"
      ```

      > [!IMPORTANT]
      > 藉由傳遞值**Y**環境變數**ACCEPT_EULA**和版本值**MSSQL_PID**，您要表達您有有效的和現有的授權，版本和您想要使用的 SQL Server 版本。 您也同意在 Docker 容器映像中執行的 SQL Server 軟體的使用會受到 SQL Server 授權條款。

      > [!NOTE]
      > 如需完整的可能值清單**MSSQL_PID**，請參閱[Linux 上的環境變數與設定 SQL Server 設定](sql-server-linux-configure-environment-variables.md)。

## <a name="connect-and-query"></a>連接及查詢

您可以連接並查詢從容器外，或是從容器中的 SQL Server 的容器。 下列各節將說明這兩種案例。 

### <a name="tools-outside-the-container"></a>容器外的工具

您可以連接到 SQL Server 執行個體在 Docker 電腦上從任何外部 Linux、 Windows 或 macOS 工具，可支援 SQL 連線。 某些常見的工具包括：

- [sqlcmd](sql-server-linux-setup-tools.md)
- [Visual Studio Code](sql-server-linux-develop-use-vscode.md)
- [Windows 上的 SQL Server Management Studio (SSMS)](sql-server-linux-manage-ssms.md)

下列範例會使用**sqlcmd**連接到 SQL Server 在 Docker 容器中執行。 連接字串中的 IP 位址是主機電腦正在執行容器的 IP 位址。

```bash
sqlcmd -S 10.3.2.4 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4 -U SA -P "<YourPassword>"
```

如果您對應不是預設的主機連接埠**1433**，將該連接埠新增至連接字串。 例如，如果您指定`-p 1400:1433`中您`docker run`命令，然後明確地連接指定通訊埠 1400。

```bash
sqlcmd -S 10.3.2.4,1400 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1400 -U SA -P "<YourPassword>"
```

### <a name="tools-inside-the-container"></a>容器內的工具

從 SQL Server 2017 CTP 2.0 [SQL Server 命令列工具](sql-server-linux-setup-tools.md)隨附的容器映像。 如果您附加至影像的互動式命令提示字元中，您可以在本機執行工具。

1. 使用 `docker exec -it` 命令在您執行的容器中啟動互動式 Bash 殼層。 在下列範例中`e69e056c702d`是容器識別碼。

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > 您不一定要指定整個容器的識別碼。您只需要指定的字元足以唯一識別它。 因此在此範例中，它可能會使用`e6`或`e69`而不是完整的識別碼。

2. 進入容器後，以 sqlcmd 進行本機連線。 請注意該 sqlcmd 不在路徑中，依預設，所以您不必指定完整路徑。

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
    ```

3. 完成後使用 sqlcmd，請輸入`exit`。

4. 完成透過互動式命令提示字元，輸入`exit`。 結束互動式 Bash 殼層後，容器會繼續執行。

## <a name="run-multiple-sql-server-containers"></a>執行多個 SQL Server 容器

Docker 可用來在同一部主機機器上執行多個 SQL Server 容器。 這是需要多個相同的主機上的 SQL Server 執行個體的方法。 每個容器必須公開本身上不同的通訊埠。

下列範例會建立兩個 SQL Server 容器，並將之對應至連接埠**1401**和**1402**主機電腦上。

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d microsoft/mssql-server-linux:2017-latest
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d microsoft/mssql-server-linux:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d microsoft/mssql-server-linux:2017-latest
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d microsoft/mssql-server-linux:2017-latest
```

現在有兩個不同的容器中執行的 SQL Server 執行個體。 用戶端可以使用容器的 Docker 主機和連接埠號碼的 IP 位址連線至每個 SQL Server 執行個體。

```bash
sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
sqlcmd -S 10.3.2.4,1402 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
sqlcmd -S 10.3.2.4,1402 -U SA -P "<YourPassword>"
```

## <a id="persist"></a> 保存您的資料

您的 SQL Server 組態變更和資料庫檔案會保存在容器即使您重新啟動的容器`docker stop`和`docker start`。 不過，如果您移除的容器`docker rm`，容器中的所有項目會遭到刪除，包括 SQL Server 和資料庫。 下列章節將說明如何使用**資料磁碟區**保存您的資料庫檔案，即使刪除相關聯的容器。

> [!IMPORTANT]
> For SQL Server，務必了解在 Docker 中的資料持續性。 除了本節中討論，請參閱 Docker 的文件上[如何管理在 Docker 容器中的資料](https://docs.docker.com/engine/tutorials/dockervolumes/)。

### <a name="mount-a-host-directory-as-data-volume"></a>為資料磁碟區掛接主機目錄

第一個選項是裝載在主機上的目錄，為您容器中的資料磁碟區。 若要這樣做，請使用`docker run`命令搭配`-v <host directory>:/var/opt/mssql`旗標。 這可讓還原容器執行之間的資料。

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
```

這項技術也可讓您共用並檢視之外 Docker 主機上的檔案。

> [!IMPORTANT]
> 在此階段不支援在 Mac 上的 Docker 的 Linux 映像上的 SQL Server 的主機磁碟區對應。 請改用資料磁碟區容器。 這項限制是特有`/var/opt/mssql`目錄。 讀取從掛接的目錄運作正常。 例如，您可以掛接主機目錄在 Mac 上使用 – v 並位於主機的.bak 檔案從備份還原。

### <a name="use-data-volume-containers"></a>使用資料磁碟區容器

第二個選項是使用資料磁碟區容器。 您可以藉由指定的磁碟區名稱，而不是與主應用程式目錄中建立資料磁碟區容器`-v`參數。 下列範例會建立名為共用的資料磁碟區**sqlvolume**。

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
```

> [!NOTE]
> 這項技術用於隱含建立的資料磁碟區中執行的命令不適用於舊版的 Docker。 在此情況下，使用 Docker 文件中所述的明確步驟[建立和掛接的資料磁碟區容器](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container)。

即使您停止並移除此容器時，保存的資料磁碟區。 您可以檢視它與`docker volume ls`命令。

```bash
docker volume ls
```

如果具有相同的磁碟區名稱，然後建立另一個容器，新的容器會使用包含磁碟區中的相同 SQL Server 資料。

若要移除資料磁碟區容器，請使用`docker volume rm`命令。

> [!WARNING]
> 如果您刪除資料磁碟區容器，容器中的任何 SQL Server 資料是*永久*刪除。

### <a name="backup-and-restore"></a>備份與還原

除了這些容器技術，您也可以使用標準的 SQL Server 備份和還原技術。 您可以使用備份檔案，來保護您的資料，或將資料移到另一個 SQL Server 執行個體。 如需詳細資訊，請參閱[Linux 上的資料庫備份和還原 SQL Server](sql-server-linux-backup-and-restore-database.md)。

> [!WARNING]
> 如果您建立備份，請確定建立或複製備份的檔案容器之外。 否則，如果容器移除時，會一併刪除的備份檔案。

## <a name="execute-commands-in-a-container"></a>在容器中執行命令

如果您有執行中的容器，您可以從終端機工作主機執行容器內的命令。

若要取得執行的容器 ID:

```bash
docker ps
```

若要啟動終端機中執行的容器 bash:

```bash
docker exec -ti <Container ID> /bin/bash
```

現在您可以執行命令，就好像您在容器內的終端機執行它們。 完成後，鍵入 `exit`。 這會結束互動式命令工作階段中，但您的容器會繼續執行。

## <a name="copy-files-from-a-container"></a>將檔案從一個容器

若要複製容器之外的檔案，請使用下列命令：

```bash
docker cp <Container ID>:<Container path> <host path>
```

**範例：**

```bash
docker cp d6b75213ef80:/var/opt/mssql/log/errorlog /tmp/errorlog
```

```PowerShell
docker cp d6b75213ef80:/var/opt/mssql/log/errorlog C:\Temp\errorlog
```

## <a name="copy-files-into-a-container"></a>將檔案複製到容器

若要將檔案複製到容器中，使用下列命令：

```bash
docker cp <Host path> <Container ID>:<Container path>
```

**範例：**

```bash
docker cp /tmp/mydb.mdf d6b75213ef80:/var/opt/mssql/data
```

```PowerShell
docker cp C:\Temp\mydb.mdf d6b75213ef80:/var/opt/mssql/data
```

## <a name="run-a-specific-sql-server-container-image"></a>執行特定的 SQL Server 容器映像

有的案例中，您可能會不使用最新的 SQL Server 容器映像。 若要執行特定的 SQL Server 容器映像，請使用下列步驟：

1. 識別 Docker**標記**您想要使用的版本。 若要檢視可用的標籤，請參閱[mssql-伺服器-linux Docker 中樞頁面](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/)。

1. 提取 SQL Server 容器映像的結束標記。 例如，若要提取 RC1 映像，取代`<image_tag>`下列命令，以及在`rc1`。

   ```bash
   docker pull microsoft/mssql-server-linux:<image_tag>
   ```

1. 若要使用該映像執行新的容器，指定中的標記名稱`docker run`命令。 在下列命令，取代`<image_tag>`與您想要執行的版本。

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d microsoft/mssql-server-linux:<image_tag>
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d microsoft/mssql-server-linux:<image_tag>
   ```

這些步驟可以用於降級現有的容器。 例如，您可能想要復原或降級基於疑難排解或測試執行中的容器。 若要降級之後執行的容器，您必須使用持續性技術資料的資料夾。 遵循相同的步驟中所述[升級 > 一節](#upgrade)，但是當您執行新的容器，請指定較舊版本的標記名稱。

> [!IMPORTANT]
> 升級和降級之間才支援 RC1 和 RC2 這一次。

## <a id="upgrade"></a> 在容器中的 SQL Server 升級

若要升級使用 Docker，容器映像，必須先找出您為升級版本的標記。 從登錄中以提取本版`docker pull`命令：

```bash
docker pull microsoft/mssql-server-linux:<image_tag>
```

這會更新您建立時，任何新容器的 SQL Server 映像，但不會更新任何執行中的容器中的 SQL Server。 若要這樣做，您必須使用最新的 SQL Server 容器映像建立新的容器，並將資料移轉到該新的容器。

1. 請確定您使用其中一個[資料持續性技術](#persist)現有的 SQL Server 容器。 這可讓您使用相同的資料開始新的容器。

1. 停止 SQL Server 容器與`docker stop`命令。

1. 建立新的 SQL Server 容器與`docker run`並指定對應的主機目錄或資料磁碟區容器。 請務必使用特定標記的 SQL Server 升級。 新的容器現在會使用新的 SQL Server 版本與現有的 SQL Server 資料。

   > [!IMPORTANT]
   > RC1、 RC2，與 GA 之間此時才支援升級。

1. 請確認您的資料庫和新的容器中的資料。

1. 選擇性地移除的舊容器`docker rm`。

## <a id="troubleshooting"></a> 疑難排解

下列各節提供在容器中執行 SQL Server 的疑難排解建議。

### <a name="docker-command-errors"></a>Docker 命令錯誤

如果發生任何錯誤`docker`命令，請確定 docker 服務正在執行，然後再次嘗試執行提高權限。

例如，on Linux，您可能會收到下列錯誤時執行`docker`命令：

```
Cannot connect to the Docker daemon. Is the docker daemon running on this host?
```

如果您在 Linux 上收到這個錯誤，請嘗試執行相同的命令前面加上`sudo`。 如果失敗，請確認 docker 服務正在執行，而且必要時啟動。

```bash
sudo systemctl status docker
sudo systemctl start docker
```

在 Windows 中，請確認您會啟動 PowerShell 或以系統管理員程式命令提示字元。

### <a name="sql-server-container-startup-errors"></a>SQL Server 容器啟動錯誤

如果執行 SQL Server 容器失敗，請嘗試下列測試：

- 如果您收到錯誤，例如 **' 無法建立端點 CONTAINER_NAME 上網路橋接器。啟動 proxy 時發生錯誤： 接聽 tcp 0.0.0.0:1433 繫結： 已經在使用中的位址。 '**，則您嘗試對應到已在使用連接埠的容器連接埠 1433。 如果您在主機電腦，在本機執行 SQL Server，也可能會發生。 它也可會發生，如果您啟動兩個 SQL Server 容器，並嘗試將其同時對應到相同的主機連接埠。 如果發生這種情況，使用`-p`參數對應到不同的主機連接埠的容器連接埠 1433。 例如： 

    ```bash
    docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d microsoft/mssql-server-linux:2017-latest`.
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d microsoft/mssql-server-linux:2017-latest`.
    ```

- 請檢查是否有任何錯誤訊息，從容器。

    ```bash
    docker logs e69e056c702d
    ```

- 請確定您符合指定的最小記憶體和磁碟需求[需求](#requirements)本主題一節。

- 如果您使用任何容器管理軟體，請確定它支援執行為根目錄的容器處理程序。 根容器中的 sqlservr 程序執行。

- 檢閱[SQL Server 安裝程式和錯誤記錄檔](#errorlogs)。

### <a name="enable-dump-captures"></a>啟用傾印擷取

如果 SQL Server 處理序失敗的容器，您應該建立新的容器使用**SYS_PTRACE**啟用。 這樣會加入追蹤處理序，也就是建立傾印檔案的例外狀況所需的 Linux 能力。 傾印檔案可供支援，以協助疑難排解問題。 下列的 docker run 命令可讓這項功能。

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d microsoft/mssql-server-linux:2017-latest
```

### <a name="sql-server-connection-failures"></a>SQL Server 連線失敗

如果您無法連線到您的容器中執行的 SQL Server 執行個體，請嘗試下列測試：

- 請確定您的 SQL Server 容器藉由查看執行**狀態**資料行`docker ps -a`輸出。 如果沒有，請使用`docker start <Container ID>`來啟動它。

- 如果您對應至非預設的主機連接埠 (不是 1433)，請確定您在連接字串中指定的連接埠。 您可以看到您的連接埠對應中**連接埠**資料行`docker ps -a`輸出。 例如，下列命令會連接到 sqlcmd 接聽通訊埠 1401容器：

    ```bash
    sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
    ```

    ```PowerShell
    sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
    ```

- 如果您使用`docker run`與現有的對應之資料磁碟區或資料磁碟區容器，SQL Server 會忽略此值的`MSSQL_SA_PASSWORD`。 相反地，從 SQL Server 中的資料在資料磁碟區或資料磁碟區容器使用的預先設定的 SA 使用者密碼。 確認您使用的您要將附加至的資料相關聯的 SA 密碼。

- 檢閱[SQL Server 安裝程式和錯誤記錄檔](#errorlogs)。

### <a name="sql-server-availability-groups"></a>SQL Server 可用性群組

如果您使用 SQL Server 可用性群組使用 Docker，有兩個額外的需求。

- 對應的連接埠，可用於複本通訊 （預設值 5022）。 例如，指定`-p 5022:5022`一部分您`docker run`命令。

- 明確地設定容器主機名稱與`-h YOURHOSTNAME`參數`docker run`命令。 設定可用性群組時，會使用這個主機名稱。 如果您未指定它與`-h`，它會預設為容器識別碼。

### <a id="errorlogs"></a> SQL Server 安裝程式和錯誤記錄檔

您可以查看 SQL Server 安裝程式和錯誤記錄檔 **/var/opt/mssql/log**。 如果容器未在執行中，第一次啟動容器。 若要檢查記錄檔，然後使用互動式命令提示字元。

```bash
docker start e69e056c702d
docker exec -it e69e056c702d "bash"
```

從您的容器內 bash 工作階段中，執行下列命令：

```bash
cd /var/opt/mssql/log
cat setup*.log
cat errorlog
```

> [!TIP]
> 如果掛接主機目錄 **/var/opt/mssql**當您建立您的容器，您可以改為查看**記錄**主機上的對應路徑的子目錄。

## <a name="next-steps"></a>後續的步驟

開始使用 docker 的 SQL Server 2017 容器映像進行[快速入門](quickstart-install-connect-docker.md)。

此外，請參閱[mssql docker GitHub 儲存機制](https://github.com/Microsoft/mssql-docker)資源、 意見反應，和已知的問題。
