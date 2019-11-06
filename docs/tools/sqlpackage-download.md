---
title: 下載並安裝 sqlpackage | Microsoft Docs
description: 下載並安裝適用於 Windows、macOS 或 Linux 的 sqlpackage
ms.custom: tools|sos
ms.date: 06/20/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
ms.openlocfilehash: f966de4951e5c90dac8d6e48f00f8de6ff067e3c
ms.sourcegitcommit: 82b70c39550402a2b0b327db32bf5ecf88b50d3c
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73033005"
---
# <a name="download-and-install-sqlpackage"></a>下載並安裝 sqlpackage

sqlpackage 在 Windows、macOS 和 Linux 上執行。

下載並安裝最新的 .NET Framework 版本以及 macOS 和 Linux 預覽：

|平台|下載|發行日期|版本|建置
|:---|:---|:---|:---|:---|
|Windows （x64）|[MSI 安裝程式](https://go.microsoft.com/fwlink/?linkid=2108813)|2019 年 10 月 29 日|18.4|15.0.4573.2|
|macOS .NET Core （x64）|[壓縮檔](https://go.microsoft.com/fwlink/?linkid=2108815)|2019 年 10 月 29 日| 18.4|15.0.4573.2|
|Linux .NET Core （x64） |[壓縮檔](https://go.microsoft.com/fwlink/?linkid=2108814)|2019 年 10 月 29 日| 18.4|15.0.4573.2|
|Windows .NET Core （x64） |[壓縮檔](https://go.microsoft.com/fwlink/?linkid=2109019)|2019 年 10 月 29 日| 18.4|15.0.4573.2|

如需最新版本的詳細資訊，請參閱[版本資訊](release-notes-sqlpackage.md)。 若要下載其他語言，請參閱[可用的語言](#available-languages)一節。

[!INCLUDE[Freshness](../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="get-sqlpackage-for-windows"></a>取得適用於 Windows 的 sqlpackage

此版本的 sqlpackage 包含標準的 Windows 安裝程式體驗，以及 .zip： 

1. 下載並執行[適用於Windows 的 DacFramework.msi 安裝程式](https://go.microsoft.com/fwlink/?linkid=2108813)。
2. 開啟新的 [命令提示字元] 視窗，然後執行 sqlpackage.exe
    - sqlpackage 會安裝到 ```C:\Program Files\Microsoft SQL Server\150\DAC\bin``` 資料夾中

## <a name="get-sqlpackage-net-core-for-windows"></a>取得適用于 Windows 的 sqlpackage .NET Core

1. 下載 [sqlpackage for Windows](https://go.microsoft.com/fwlink/?linkid=2109019)。
2. 以滑鼠右鍵按一下 Windows Explorer 中的檔案，然後選取 [解壓縮全部]，然後選取目標目錄，來解壓縮檔案。
3. 開啟新的終端機視窗，並將 cd 放到解壓縮 sqlpackage 的位置：

   ```cmd
   > sqlpackage
   ```

## <a name="get-sqlpackage-net-core-for-macos"></a>取得適用于 macOS 的 sqlpackage .NET Core

1. 下載[適用於 macOS 的 sqlpackage](https://go.microsoft.com/fwlink/?linkid=2108815)。
2. 若要將檔案解壓縮並啟動 sqlpackage，請開啟新的終端機視窗並輸入下列命令：

   ```bash
   $ mkdir sqlpackage
   $ unzip ~/Downloads/sqlpackage-osx-<version string>.zip ~/sqlpackage 
   $ echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   $ source ~/.bash_profile
   $ sqlpackage
   ```

## <a name="get-sqlpackage-net-core-for-linux"></a>取得適用于 Linux 的 sqlpackage .NET Core

1. 使用其中一種安裝程式或 tar.gz 封存下載[適用於 Linux 的 sqlpackage](https://go.microsoft.com/fwlink/?linkid=2108814)：
2. 若要將檔案解壓縮並啟動 sqlpackage，請開啟新的終端機視窗並輸入下列命令：

   ```bash
   cd ~
   $ mkdir sqlpackage
   $ unzip ~/Downloads/sqlpackage-linux-<version string>.zip -d ~/sqlpackage 
   $ echo "export PATH=\"\$PATH:$HOME/sqlpackage\"" >> ~/.bashrc
   $ chmod a+x ~/sqlpackage/sqlpackage
   $ source ~/.bashrc
   $ sqlpackage
   ```

   > [!NOTE]
   > 在 Debian、Redhat 和 Ubuntu 上，您可能遺失相依性。 使用下列命令，根據您的 Linux 版本安裝這些相依性：

   **Debian：**

   ```bash
   $ sudo apt-get install libunwind8
   ```

   **Redhat:**

   ```bash
   $ yum install libunwind
   $ yum install libicu
   ```

   **Ubuntu:**

   ```bash
   $ sudo apt-get install libunwind8

   # install the libicu library based on the Ubuntu version
   $ sudo apt-get install libicu52      # for 14.x
   $ sudo apt-get install libicu55      # for 16.x
   $ sudo apt-get install libicu57      # for 17.x
   $ sudo apt-get install libicu60      # for 18.x
   ```

## <a name="uninstall-sqlpackage-preview"></a>解除安裝 sqlpackage (預覽)

如果您使用 Windows 安裝程式安裝 sqlpackage，請使用與刪除任何 Windows 應用程式相同的方式解除安裝。

如果您使用 .zip 或其他封存安裝 sqlpackage，請刪除這些檔案。

## <a name="supported-operating-systems"></a>支援的作業系統

sqlpackage 在 Windows、macOS 和 Linux 上執行，並支援下列平台：

### <a name="windows"></a>Windows

- Windows 10
- Windows 8.1
- Windows 7 SP1
- Windows Server 2008 R2
- Windows Server 2012 R2
- Windows Server 2016

### <a name="macos"></a>macOS

- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux-x64"></a>Linux (x64)

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="available-languages"></a>可用語言

此版本的 sqlpackage 提供下列語言版本：

sqlpackage 視窗：  
[簡體中文](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x40a)

sqlpackage .NET Core 視窗：  
[簡體中文](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x40a)

sqlpackage .NET Core macOS：  
[簡體中文](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x40a)

sqlpackage .NET Core Linux：  
[簡體中文](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x40a)

## <a name="next-steps"></a>Next Steps

- 深入了解 [sqlpackage](sqlpackage.md)

[Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)
