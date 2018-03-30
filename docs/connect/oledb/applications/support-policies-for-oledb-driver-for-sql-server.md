---
title: SQL Server 的 OLE DB 驅動程式的支援原則 |Microsoft 文件
description: SQL Server 的 OLE DB 驅動程式的支援原則
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 250b0dce301190454a911f5409425f486286047b
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2018
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>SQL Server 的 OLE DB 驅動程式的支援原則
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  本文將討論如何各種資料存取元件可以搭配 OLE DB 驅動程式的 SQL Server。  

## <a name="server-support"></a>伺服器支援  
 OLE DB 驅動程式的 SQL Server 支援連接至[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]， [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]，[!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)]， [!INCLUDE[ssSQL17](../../../includes/sssql17-md.md)]，和[!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)]。

## <a name="supported-operating-system-versions"></a>支援的作業系統版本  
 下表列出 SQL Server 中的使用哪些作業系統支援 OLE DB 驅動程式。  

|支援的作業系統|  
|--------------------------------------|---------------------------------|   
|Microsoft Windows 8.1<br /><br />Microsoft Windows 10<br /><br /> Microsoft Windows Server 2012<br /><br />Microsoft Windows Server 2012 R2<br /><br />Microsoft Windows Server 2016|  

## <a name="ado-support-policies"></a>ADO 支援原則  
 如果 ADO 應用程式不需要 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 或更新版本的任何功能，就可以使用 Windows 隨附的 SQLOLEDB OLE DB 提供者。  

 ADO 應用程式可以使用 SQL Server 的 OLE DB 驅動程式，但如果它們這樣必須指定`DataTypeCompatibility=80`的連接字串中。 當連接字串中存在 `DataTypeCompatibility=80` 時，只能使用 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 的功能。  

## <a name="ole-db-support-policies"></a>OLE DB 支援原則  
應用程式可以使用 Windows 作業系統隨附的 OLE DB 提供者 (SQLOLEDB)。 不過，，處於維護模式，而且不會再更新。 您應該改用 OLE DB 驅動程式的 SQL Server (MSOLEDBSQL)。

## <a name="see-also"></a>另請參閱  
 [使用 OLE DB 驅動程式的 SQL Server 的建立應用程式](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
