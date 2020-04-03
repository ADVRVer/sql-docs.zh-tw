---
title: OLE DB Driver for SQL Server 的支援原則 | Microsoft Docs
description: OLE DB Driver for SQL Server 的支援原則
ms.date: 03/18/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.custom: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 3f48aa8c68b364db98d1cd3111c11c6635ee5335
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "79526823"
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server 的支援原則
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

此文章討論如何搭配 OLE DB Driver for SQL Server 使用各種資料存取元件。  

## <a name="sql-version-support"></a>SQL 版本支援  

OLE DB Driver for SQL Server 已經過測試，並支援下列 SQL Server 版本的連線。

| 驅動程式版本 | Azure SQL Database | Azure SQL DW | Azure SQL 受控執行個體 | SQL Server 2019 | SQL Server 2017 | SQL Server 2016 | SQL Server 2014 | SQL Server 2012 |
|----|-|-|-|-|-|-|-|-|
|18.3|Y|Y|Y|Y|Y|Y|Y|Y|
|18.2|Y|Y|Y|Y|Y|Y|Y|Y|
|18.1|Y|Y|Y| |Y|Y|Y|Y|
|18.0|Y|Y|Y| |Y|Y|Y|Y|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

## <a name="supported-operating-system-versions"></a>支援的作業系統版本  

下表列出 OLE DB Driver for SQL Server 支援哪些作業系統。  

| 驅動程式版本 | Windows Server 2019 | Windows Server 2016 | Windows Server 2012<sup>1</sup> | Windows Server 2012 R2<sup>2</sup> | Windows 10 | Windows 8.1<sup>3</sup> |
|----|-|-|-|-|-|-|
|18.3|Y|Y|Y|Y|Y|Y|
|18.2|Y|Y|Y|Y|Y|Y|
|18.1| |Y|Y|Y|Y|Y|
|18.0| |Y|Y|Y|Y|Y|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

<sup>1</sup> 支援 Windows Server 2012 (含 [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061))。  
<sup>2</sup> 支援 Windows Server 2012 R2 (含 [2014 年 4 月更新](https://go.microsoft.com/fwlink/?linkid=2073785)和 [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061))。  
<sup>3</sup> 支援 Windows 8.1 (含 [2014 年 4 月更新](https://go.microsoft.com/fwlink/?linkid=2073785)和 [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061))。  

> [!NOTE]  
> 不支援在 Windows 上使用 UTF-8 字碼頁 (「使用 Unicode UTF-8 取得全球語言支援」)。

## <a name="ado-support-policies"></a>ADO 支援原則  

如果 ADO 應用程式不需要 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 或更新版本的任何功能，就可以使用 Windows 隨附的 SQLOLEDB OLE DB 提供者。  

ADO 應用程式可以使用 OLE DB Driver for SQL Server，但是使用時，必須在連接字串中指定 `DataTypeCompatibility=80`。 當連接字串中存在 `DataTypeCompatibility=80` 時，只能使用 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 的功能。  

## <a name="ole-db-support-policies"></a>OLE DB 支援原則  

應用程式應該使用 Windows 作業系統隨附的 OLE DB 提供者 (SQLOLEDB)。 不過，這處於維護模式，且不再更新。 請改為使用 OLE DB Driver for SQL Server (MSOLEDBSQL)。

## <a name="see-also"></a>另請參閱  

[使用 OLE DB Driver for SQL Server 建置應用程式](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)
