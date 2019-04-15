---
title: 系統需求 (ODBC Driver for SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 02/15/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- prerequisites
- system requirements
- requirements
ms.assetid: f03b7fdd-0e9d-4e74-958d-e8c87e027348
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2b4aca8fcd4f18f6e70c9e6f98b415402e19621
ms.sourcegitcommit: 3cfedfeba377560d460ca3e42af1e18824988c07
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59042317"
---
# <a name="system-requirements"></a>系統需求
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

本主題列出使用 Linux 和 macOS 版 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的需求。


## <a name="microsoft-odbc-driver-13-131-and-17-for-sql-server"></a>Microsoft ODBC Driver 13、13.1 和 17 for SQL Server

Linux 和 macOS 驅動程式僅適用於下列作業系統的 64 位元版本︰

|作業系統|支援的驅動程式版本|
|------------------------------------|--------------------------------|
|Apple OS X 10.11 (El Capitan)|13、13.1、17|
|Apple macOS 10.12 (Sierra)|13、13.1、17|
|Apple macOS 10.13 (High Sierra)|17| 
|Apple macOS 10.14 (Mojave)|17| 
|Debian Linux 8|13、13.1、17|
|Debian Linux 9|17|
|RedHat Enterprise Linux 6|13、13.1、17|
|RedHat Enterprise Linux 7|13、13.1、17|
|SuSE Linux Enterprise Server 11|13、13.1、17 <br /><br /> **注意：** ODBC Driver 17 僅支援 SuSE Linux Enterprise Server 11 SP4|
|SuSE Linux Enterprise Server 12|13、13.1、17|
|SuSE Linux Enterprise Server 15|17|
|Ubuntu Linux 14.04|13、13.1、17|
|Ubuntu Linux 15.10|13、13.1|
|Ubuntu Linux 16.04|13、13.1、17|
|Ubuntu Linux 16.10|13、13.1|
|Ubuntu Linux 17.04|17| 
|Ubuntu Linux 17.10|17|
|Ubuntu Linux 18.04|17| 
|Ubuntu Linux 18.10|17| 

Linux 和 macOS 上 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 13、13.1 及 17 的安裝套件，可在使用散發套件的套件管理系統安裝時，能夠自動解析驅動程式的相依性，如[安裝驅動程式](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)中所述。

## <a name="microsoft-odbc-driver-11-for-sql-server"></a>Microsoft ODBC Driver 11 for SQL Server  
  
-   64 位元 UnixODBC 2.3.0 驅動程式管理員 (針對 64 位元 SQLLEN/SQLULEN 建置)。 Linux 上的 ODBC 驅動程式不支援較新版本的 64 位元 UnixODBC 驅動程式管理員。 如需相關資訊，請參閱 [Installing the Driver Manager](../../../connect/odbc/linux-mac/installing-the-driver-manager.md) 。  
  
-   **Red Hat Enterprise Linux 5 (64 位元)** 的 ODBC 驅動程式需要下列套件，而且可以在這裡下載：[Microsoft ODBC Driver 11 for SQL Server - Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321)  
    -   `glibc`  
    -   `libgcc`  
    -   `libstdc++`  
    -   `e2fsprogs-libs`  
    -   `krb5-libs`  
    -   `openssl`  
  
-   **Red Hat Enterprise Linux 6 (64 位元)** 的 ODBC 驅動程式需要下列套件，而且可以在這裡下載：[Microsoft ODBC Driver 11 for SQL Server - Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321)  
    -   `glibc`  
    -   `libgcc`  
    -   `libstdc++`  
    -   `libuuid`  
    -   `krb5-libs`  
    -   `openssl`  
  
-   **SUSE Linux Enterprise 11 Service Pack 2 (64 位元)** 的 ODBC 驅動程式需要下列套件，而且可以在這裡下載：[Microsoft ODBC Driver 11 (預覽) for SQL Server - SUSE Linux](https://go.microsoft.com/fwlink/?LinkId=264916)  
    -   `glibc`  
    -   `libstdc++46`  
    -   `libgcc46`  
    -   `libuuid1`  
    -   `krb5`  
    -   `libopenssl0_9_8`  
  
## <a name="see-also"></a>另請參閱
[安裝驅動程式管理員](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)

[此驅動程式版本的已知問題](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)  

[版本資訊](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)  
