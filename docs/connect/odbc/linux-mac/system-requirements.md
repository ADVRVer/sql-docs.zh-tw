---
title: "系統需求 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- prerequisites
- system requirements
- requirements
ms.assetid: f03b7fdd-0e9d-4e74-958d-e8c87e027348
caps.latest.revision: "31"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 8bf81a5a5be0f5d276946b6f722c1875922b2155
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="system-requirements"></a>系統需求
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

本主題列出使用的需求[!INCLUDE[msCoName](../../../includes/msconame_md.md)]ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Linux 及 macOS 上。

## <a name="microsoft-odbc-driver-13-and-131-for-sql-server"></a>Microsoft ODBC Driver 13 / 13.1 for SQL Server

僅適用於下列作業系統的 64 位元版本的 Linux 及 macOS 驅動程式︰

- Apple macOS 10.12 （利也）
- Apple OS X 10.11 (El Capitan)
- Debian Linux 8
- RedHat Enterprise Linux 6
- RedHat Enterprise Linux 7
- SuSE Linux Enterprise Server 11
- SuSE Linux Enterprise Server 12
- Ubuntu Linux 14.04
- Ubuntu Linux 15.10
- Ubuntu Linux 16.04
- Ubuntu Linux 16.10

安裝封裝的[!INCLUDE[msCoName](../../../includes/msconame_md.md)]ODBC Driver 13 和 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Linux 及 macOS 解決驅動程式的相依性中所述使用您散發的封裝管理系統的安裝時自動[安裝驅動程式](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)。

## <a name="microsoft-odbc-driver-11-for-sql-server"></a>Microsoft ODBC Driver 11 for SQL Server  
  
-   64 位元 UnixODBC 2.3.0 驅動程式管理員 (針對 64 位元 SQLLEN/SQLULEN 建置)。 Linux 上的 ODBC 驅動程式不支援較新版本的 64 位元 UnixODBC 驅動程式管理員。 如需相關資訊，請參閱 [Installing the Driver Manager](../../../connect/odbc/linux-mac/installing-the-driver-manager.md) 。  
  
-   ODBC 驅動程式**Red Hat Enterprise Linux 5 （64 位元）**需要下列封裝，而且可以在這裡下載： [Microsoft ODBC Driver 11 for SQL Server-Red Hat Linux](http://go.microsoft.com/fwlink/?LinkId=267321)  
    -   glibc  
    -   libgcc  
    -   libstdc++  
    -   e2fsprogs-libs  
    -   krb5-libs  
    -   openssl  
  
-   ODBC 驅動程式**Red Hat Enterprise Linux 6 （64 位元）**需要下列封裝，而且可以在這裡下載： [Microsoft ODBC Driver 11 for SQL Server-Red Hat Linux](http://go.microsoft.com/fwlink/?LinkId=267321)  
    -   glibc  
    -   libgcc  
    -   libstdc++  
    -   libuuid  
    -   krb5-libs  
    -   openssl  
  
-   ODBC 驅動程式**SUSE Linux Enterprise 11 Service Pack 2 （64 位元）**需要下列封裝，而且可以在這裡下載： [Microsoft ODBC Driver 11 Preview for SQL Server-SUSE Linux](http://go.microsoft.com/fwlink/?LinkId=264916)  
    -   glibc  
    -   libstdc++46  
    -   libgcc46  
    -   libuuid1  
    -   krb5  
    -   libopenssl0_9_8  
  
## <a name="see-also"></a>請參閱＜
[安裝驅動程式管理員](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)

[此驅動程式版本的已知問題](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)  

[版本資訊](../../../connect/odbc/linux-mac/release-notes.md)  
