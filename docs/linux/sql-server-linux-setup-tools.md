---
title: 在 Linux 上安裝 SQL Server 命令列工具
titleSuffix: SQL Server
description: 本文說明如何在 Linux 上安裝 SQL Server 工具。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 06/07/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sqlfreshmay19
ms.technology: linux
ms.assetid: eff8e226-185f-46d4-a3e3-e18b7a439e63
ms.openlocfilehash: d6e10c384d799ee416facee150e5e2318b381ea6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "66810275"
---
# <a name="install-sqlcmd-and-bcp-the-sql-server-command-line-tools-on-linux"></a>Sqlcmd 和 bcp 的 SQL Server 命令列工具在 Linux 上安裝

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

下列步驟安裝命令列工具，Microsoft ODBC 驅動程式及其相依性。 **Mssql 工具**套件包含：

- **sqlcmd**:查詢命令列公用程式。
- **bcp**:大量匯入 / 匯出公用程式。

安裝適用於您的平台的工具：

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)
- [macOS](#macos)
- [Docker](#docker)

本文說明如何安裝命令列工具。 如果您要尋找的範例，示範如何使用**sqlcmd**或是**bcp**，請參閱[連結](#next-steps)本主題結尾處。

## <a name="a-idrhelainstall-tools-on-rhel-7"></a><a id="RHEL"><a/>在 RHEL 7 上安裝工具

使用下列步驟來安裝**mssql 工具**Red Hat Enterprise Linux 上。 

1. 進入進階使用者模式。

   ```bash
   sudo su
   ```

1. 下載 Microsoft Red Hat 存放庫的組態檔。

   ```bash
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/msprod.repo
   ```

1. 結束超級使用者模式。

   ```bash
   exit
   ```

1. 如果您有舊版**mssql 工具**安裝，請移除任何舊版 unixODBC 套件。

   ```bash
   sudo yum remove mssql-tools unixODBC-utf16-devel
   ```

1. 執行下列命令來安裝**mssql 工具**unixODBC 開發人員套件。

   ```bash
   sudo yum install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > 若要更新至最新版本**mssql 工具**執行下列命令：
   >    ```bash
   >   sudo yum check-update
   >   sudo yum update mssql-tools
   >   ```

1. **選擇性**:新增`/opt/mssql-tools/bin/`至您**路徑**bash 殼層中的環境變數。

   若要讓**sqlcmd/bcp**存取從 bash 殼層中的登入工作階段中，修改您**路徑**中 **~/.bash_profile**檔案使用下列命令：

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   若要讓**sqlcmd/bcp**從 bash 殼層中互動式/非登入工作階段，可存取修改**路徑**中 **~/.bashrc**檔案使用下列命令：

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="ubuntu"></a>在 Ubuntu 16.04 上安裝工具

使用下列步驟來安裝**mssql 工具**在 Ubuntu 上。 

1. 匯入公用存放庫 GPG 金鑰。

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. 註冊 Microsoft Ubuntu 存放庫。

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
   ```

1. 更新 [來源] 清單並執行安裝命令與 unixODBC 開發人員套件。

   ```bash
   sudo apt-get update 
   sudo apt-get install mssql-tools unixodbc-dev
   ```

   > [!Note] 
   > 若要更新至最新版本**mssql 工具**執行下列命令：
   >    ```bash
   >   sudo apt-get update 
   >   sudo apt-get install mssql-tools 
   >   ```

1. **選擇性**:新增`/opt/mssql-tools/bin/`至您**路徑**bash 殼層中的環境變數。

   若要讓**sqlcmd/bcp**存取從 bash 殼層中的登入工作階段中，修改您**路徑**中 **~/.bash_profile**檔案使用下列命令：

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   若要讓**sqlcmd/bcp**從 bash 殼層中互動式/非登入工作階段，可存取修改**路徑**中 **~/.bashrc**檔案使用下列命令：

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="SLES"></a>在 SLES 12 上安裝工具

使用下列步驟來安裝**mssql 工具**SUSE Linux Enterprise Server 上。 

1. Microsoft SQL Server 儲存機制加入 Zypper。

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. 安裝**mssql 工具**unixODBC 開發人員套件。

   ```bash
   sudo zypper install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > 若要更新至最新版本**mssql 工具**執行下列命令：
   >    ```bash
   >   sudo zypper refresh
   >   sudo zypper update mssql-tools
   >   ```

1. **選擇性**:新增`/opt/mssql-tools/bin/`至您**路徑**bash 殼層中的環境變數。

   若要讓**sqlcmd/bcp**存取從 bash 殼層中的登入工作階段中，修改您**路徑**中 **~/.bash_profile**檔案使用下列命令：

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   若要讓**sqlcmd/bcp**從 bash 殼層中互動式/非登入工作階段，可存取修改**路徑**中 **~/.bashrc**檔案使用下列命令：

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="macos"></a> 在 macOS 上安裝工具

預覽**sqlcmd**並**bcp** macOS 上現已提供。 如需詳細資訊，請參閱 <<c0> [ 公告](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/16/sql-server-command-line-tools-for-macos-released/)。

*安裝[Homebrew](https://brew.sh)如果您還沒有這個：*

        /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

若要安裝適用於 Mac El Capitan 和 Sierra 工具，使用下列命令：

```
# brew untap microsoft/mssql-preview if you installed the preview version 
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install mssql-tools
#for silent install: 
#HOMEBREW_NO_ENV_FILTERING=1 ACCEPT_EULA=y brew install mssql-tools
```

## <a id="docker"></a> Docker

Docker 映像中包含 SQL Server 命令列工具。 如果您附加至互動式命令提示字元使用映像，您可以在本機執行的工具。

## <a name="offline-installation"></a>離線安裝

[!INCLUDE[SQL Server Linux offline package installation](../includes/sql-server-linux-offline-package-install-intro.md)]

1. 首先，尋找並複製**mssql 工具**您 Linux 散發套件的套件：

   | Linux 散發套件 | **mssql 工具**封裝位置 |
   |---|---|
   | Red Hat | [https://packages.microsoft.com/rhel/7.3/prod](https://packages.microsoft.com/rhel/7.3/prod) |
   | SLES | [https://packages.microsoft.com/sles/12/prod](https://packages.microsoft.com/sles/12/prod)|
   | Ubuntu 16.04 | [https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/mssql-tools](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/mssql-tools) |

1. 也會尋找並複製**msodbcsql**封裝，也就是相依性。 **Msodbcsql**封裝也會相依於其中一個**unixODBC devel** （Red Hat 和 SLES） 或**unixodbc-dev** (Ubuntu)。 位置**msodbcsql**下表列出封裝：

   | Linux 散發套件 | ODBC 套件位置 |
   |---|---|
   | Red Hat | [https://packages.microsoft.com/rhel/7.3/prod](https://packages.microsoft.com/rhel/7.3/prod) |
   | SLES | [https://packages.microsoft.com/sles/12/prod](https://packages.microsoft.com/sles/12/prod)|
   | Ubuntu 16.04 | [**msodbcsql**](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql)<br/>[**unixodbc-dev**](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/u/unixodbc/) |

1. **將下載的套件移至您的 Linux 機器**。 如果您使用不同的電腦下載的套件時，將封裝移到您的 Linux 機器的一個方法是使用**scp**命令。

1. **安裝和封裝**:安裝**mssql 工具**並**msodbc**封裝。 如果您收到的任何相依性錯誤，請忽略它們，直到下一個步驟。

    | 平台 | 套件安裝命令 |
    |-----|-----|
    | Red Hat | `sudo yum localinstall msodbcsql-<version>.rpm`<br/>`sudo yum localinstall mssql-tools-<version>.rpm` |
    | SLES | `sudo zypper install msodbcsql-<version>.rpm`<br/>`sudo zypper install mssql-tools-<version>.rpm` |
    | Ubuntu | `sudo dpkg -i msodbcsql_<version>.deb`<br/>`sudo dpkg -i mssql-tools_<version>.deb` |

1. **解決遺失的相依性**:您可能必須在此時遺失相依性。 如果沒有，您可以略過此步驟。 在某些情況下，您必須手動尋找並安裝這些相依性。

    RPM 套件，您可以檢查必要的相依性，使用下列命令：

    ```bash
    rpm -qpR msodbcsql-<version>.rpm
    rpm -qpR mssql-tools-<version>.rpm
    ```

    Debian 套件，如果您有存取權已核准的存放庫包含這些相依性，最簡單的解決方案是使用**apt get**命令：

    ```bash
    sudo apt-get -f install
    ```

    > [!NOTE]
    > 此命令完成的 SQL Server 套件的安裝。

    如果這不適用於您的 Debian 套件，您可以檢查必要的相依性，使用下列命令：

    ```bash
    dpkg -I msodbcsql_<version>_amd64.deb | grep "Depends:"
    dpkg -I mssql-tools_<version>_amd64.deb | grep "Depends:"
    ```

## <a name="next-steps"></a>後續步驟

如需如何使用的範例**sqlcmd**若要連接到 SQL Server，並建立資料庫，請參閱下列快速入門：

- [在 Red Hat Enterprise Linux 上安裝](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server 上安裝](quickstart-install-connect-suse.md)
- [在 Ubuntu 上安裝](quickstart-install-connect-ubuntu.md)
- [在 Docker 上執行](quickstart-install-connect-ubuntu.md)

如需如何使用的範例**bcp**大量匯入和匯出資料，請參閱[大量複製資料到 Linux 上的 SQL Server](sql-server-linux-migrate-bcp.md)。
