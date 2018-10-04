---
title: OLE DB Driver for SQL Server 的支援原則 | Microsoft Docs
description: OLE DB Driver for SQL Server 的支援原則
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.custom: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 140bd1e82540ab7f8869ae64173d7d5431ea9233
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47774736"
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server 的支援原則
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  這篇文章討論各種資料存取元件可以搭配 OLE DB Driver for SQL Server。  

## <a name="server-support"></a>伺服器支援  
 OLE DB Driver for SQL Server 支援連接至[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]， [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]，[!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)]， [!INCLUDE[ssSQL17](../../../includes/sssql17-md.md)]，和[!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)]。

## <a name="supported-operating-system-versions"></a>支援的作業系統版本  
 下表列出哪些作業系統支援 OLE DB Driver for SQL Server。  

|支援的作業系統|  
|--------------------------------------|---------------------------------|   
|Microsoft Windows 8.1<br /><br />Microsoft Windows 10<br /><br /> Microsoft Windows Server 2012<br /><br />Microsoft Windows Server 2012 R2<br /><br />Microsoft Windows Server 2016|  

## <a name="ado-support-policies"></a>ADO 支援原則  
 如果 ADO 應用程式不需要 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 或更新版本的任何功能，就可以使用 Windows 隨附的 SQLOLEDB OLE DB 提供者。  

 ADO 應用程式可以使用 OLE DB Driver for SQL Server，但如果它們這樣必須同時指定`DataTypeCompatibility=80`連接字串中。 當連接字串中存在 `DataTypeCompatibility=80` 時，只能使用 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 的功能。  

## <a name="ole-db-support-policies"></a>OLE DB 支援原則  
應用程式應該使用 Windows 作業系統隨附的 OLE DB 提供者 (SQLOLEDB)。 不過，，處於維護模式，而且不會再更新。 您應該改用 OLE DB Driver for SQL Server (MSOLEDBSQL)。

## <a name="see-also"></a>另請參閱  
 [利用 OLE DB Driver for SQL Server 建置](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
