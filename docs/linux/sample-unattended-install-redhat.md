---
title: Red Hat Enterprise Linux 上的 SQL Server 的自動的安裝
titleSuffix: SQL Server
description: SQL Server 指令碼範例-在 Red Hat Enterprise Linux 上的自動安裝
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: e72c027f9426376ab79f29067385d2c4a8910a9b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "66713532"
---
# <a name="sample-unattended-sql-server-installation-script-for-red-hat-enterprise-linux"></a>範例：Red Hat Enterprise linux 的自動安裝的 SQL Server 安裝指令碼

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

此範例 Bash 指令碼會安裝 SQL Server 2017 上 Red Hat Enterprise Linux (RHEL) 不需要互動式輸入。 它提供的安裝 database engine、 SQL Server 命令列工具，SQL Server Agent 的範例，並執行後續安裝步驟。 或者，您可以安裝全文檢索搜尋，並建立系統管理使用者。

> [!TIP]
> 如果您不需要自動的安裝指令碼，安裝 SQL Server 的最快方式是遵循[Red Hat 的快速入門](quickstart-install-connect-red-hat.md)。 其他安裝資訊，請參閱[在 Linux 上的 SQL Server 的安裝指引](sql-server-linux-setup.md)。

## <a name="prerequisites"></a>先決條件

- 您需要至少 2 GB 的記憶體，在 Linux 上執行 SQL Server。
- 必須是檔案系統**XFS**或是**EXT4**。 其他檔案系統，例如**BTRFS**，不支援。
- 如需其他系統需求，請參閱[在 Linux 上的 SQL Server 的系統需求](sql-server-linux-setup.md#system)。

## <a name="sample-script"></a>範例指令碼
範例指令碼儲存至檔案，並進行自訂，取代指令碼中的變數值。 您也可以設定任何指令碼變數設為環境變數，只要您移除指令碼檔案。

```bash
#!/bin/bash -e

# Use the following variables to control your install:

# Password for the SA user (required)
MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>'

# Product ID of the version of SQL server you're installing
# Must be evaluation, developer, express, web, standard, enterprise, or your 25 digit product key
# Defaults to developer
MSSQL_PID='evaluation'

# Install SQL Server Agent (recommended)
SQL_ENABLE_AGENT='y'

# Install SQL Server Full Text Search (optional)
# SQL_INSTALL_FULLTEXT='y'

# Create an additional user with sysadmin privileges (optional)
# SQL_INSTALL_USER='<Username>'
# SQL_INSTALL_USER_PASSWORD='<YourStrong!Passw0rd>'

if [ -z $MSSQL_SA_PASSWORD ]
then
  echo Environment variable MSSQL_SA_PASSWORD must be set for unattended install
  exit 1
fi

echo Adding Microsoft repositories...
sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo

echo Installing SQL Server...
sudo yum install -y mssql-server

echo Running mssql-conf setup...
sudo MSSQL_SA_PASSWORD=$MSSQL_SA_PASSWORD \
     MSSQL_PID=$MSSQL_PID \
     /opt/mssql/bin/mssql-conf -n setup accept-eula

echo Installing mssql-tools and unixODBC developer...
sudo ACCEPT_EULA=Y yum install -y mssql-tools unixODBC-devel

# Add SQL Server tools to the path by default:
echo Adding SQL Server tools to your path...
echo PATH="$PATH:/opt/mssql-tools/bin" >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc

# Optional Enable SQL Server Agent :
if [ ! -z $SQL_ENABLE_AGENT ]
then
  echo Enable SQL Server Agent...
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
  sudo systemctl restart mssql-server
fi

# Optional SQL Server Full Text Search installation:
if [ ! -z $SQL_INSTALL_FULLTEXT ]
then
    echo Installing SQL Server Full-Text Search...
    sudo yum install -y mssql-server-fts
fi

# Configure firewall to allow TCP port 1433:
echo Configuring firewall to allow traffic on port 1433...
sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
sudo firewall-cmd --reload

# Example of setting post-installation configuration options
# Set trace flags 1204 and 1222 for deadlock tracing:
#echo Setting trace flags...
#sudo /opt/mssql/bin/mssql-conf traceflag 1204 1222 on

# Restart SQL Server after making configuration changes:
echo Restarting SQL Server...
sudo systemctl restart mssql-server

# Connect to server and get the version:
counter=1
errstatus=1
while [ $counter -le 5 ] && [ $errstatus = 1 ]
do
  echo Waiting for SQL Server to start...
  sleep 5s
  /opt/mssql-tools/bin/sqlcmd \
    -S localhost \
    -U SA \
    -P $MSSQL_SA_PASSWORD \
    -Q "SELECT @@VERSION" 2>/dev/null
  errstatus=$?
  ((counter++))
done

# Display error if connection failed:
if [ $errstatus = 1 ]
then
  echo Cannot connect to SQL Server, installation aborted
  exit $errstatus
fi

# Optional new user creation:
if [ ! -z $SQL_INSTALL_USER ] && [ ! -z $SQL_INSTALL_USER_PASSWORD ]
then
  echo Creating user $SQL_INSTALL_USER
  /opt/mssql-tools/bin/sqlcmd \
    -S localhost \
    -U SA \
    -P $MSSQL_SA_PASSWORD \
    -Q "CREATE LOGIN [$SQL_INSTALL_USER] WITH PASSWORD=N'$SQL_INSTALL_USER_PASSWORD', DEFAULT_DATABASE=[master], CHECK_EXPIRATION=ON, CHECK_POLICY=ON; ALTER SERVER ROLE [sysadmin] ADD MEMBER [$SQL_INSTALL_USER]"
fi

echo Done!
```

## <a name="running-the-script"></a>執行指令碼

執行指令碼

1. 將範例貼到 慣用的文字編輯器，並儲存為令人印象深刻的名稱，例如`install_sql.sh`。

1. 來自訂`MSSQL_SA_PASSWORD`， `MSSQL_PID`，以及任何其他您想要變更的變數。

1. 指令碼標示為可執行檔

   ```bash
   chmod +x install_sql.sh
   ```

1. 執行指令碼

   ```bash
   ./install_sql.sh
   ```

## <a name="understanding-the-script"></a>了解指令碼

Bash 指令碼會執行第一件事是設定一些變數。  這些可以是指令碼變數，例如此範例中或環境變數。  變數`MSSQL_SA_PASSWORD`已**必要**由 SQL Server 安裝，有些則是自訂建立指令碼的變數。  範例指令碼會執行下列步驟：

1. 匯入公用 Microsoft GPG 金鑰。

1. 註冊 Microsoft 存放庫，適用於 SQL Server 和的命令列工具。

1. 更新本機存放庫

1. 安裝 SQL Server

1. 設定 SQL Server 與```MSSQL_SA_PASSWORD```並自動接受使用者授權合約。

1. 自動接受使用者授權合約，如 SQL Server 命令列工具，加以安裝，而且安裝 unixodbc 開發套件。

1. 為了方便使用的路徑中加入 SQL Server 命令列工具。

1. 如果安裝 SQL Server Agent 的指令碼變數```SQL_INSTALL_AGENT```，在預設設定。

1. 選擇性地安裝 SQL Server 全文檢索搜尋，如果變數```SQL_INSTALL_FULLTEXT```設定。

1. 解除封鎖 tcp 系統在防火牆上，從另一個系統連線至 SQL Server 所需的連接埠 1433年。

1. 選擇性地設定死結追蹤的追蹤旗標。 （需要幾行取消註解）

1. 現在已安裝 SQL Server，才能讓它運作，重新啟動程序。

1. 確認 SQL Server 已正確安裝，同時隱藏任何錯誤訊息。

1. 建立新的伺服器系統管理員使用者，如果```SQL_INSTALL_USER```和```SQL_INSTALL_USER_PASSWORD```同時設定。

## <a name="next-steps"></a>後續步驟

簡化多個自動的安裝和建立獨立的 Bash 指令碼，以設定適當的環境變數。  您可以移除任何變數的範例指令碼使用，並將它們放在自己的 Bash 指令碼。

```bash
#!/bin/bash
export MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>'
export MSSQL_PID='evaluation'
export SQL_INSTALL_AGENT='y'
export SQL_INSTALL_USER='<Username>'
export SQL_INSTALL_USER_PASSWORD='<YourStrong!Passw0rd>'
export SQL_INSTALL_AGENT='y'
```

然後執行 Bash 指令碼，如下所示：
```bash
. ./my_script_name.sh
```

在 Linux 上 SQL Server 的相關資訊，請參閱[SQL Server on Linux 概觀](sql-server-linux-overview.md)。
