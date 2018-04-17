---
title: 準備命令 |Microsoft 文件
description: 準備適用於 SQL Server 使用 OLE DB 驅動程式的命令
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, commands
- prepared statements [OLE DB Driver for SQL Server]
- commands [OLE DB]
- command preparation [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 55dd38bef585a473f7c84504d9d0263808e099b8
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2018
---
# <a name="preparing-commands"></a>準備命令
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQL Server OLE DB 驅動程式支援針對單一命令; 的最佳化多次執行命令的準備不過，命令準備會產生負擔，而且取用者不需要準備命令，命令執行一次以上。 一般而言，如果某個命令將執行三次以上，您就應該準備此命令。  
  
 基於效能的考量，命令準備會延遲到執行命令為止。 這是預設行為。 在執行命令或執行中繼屬性作業之前，無法得知正在準備之命令中的任何錯誤。 將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 屬性 SSPROP_DEFERPREPARE 設定為 FALSE 可以關閉此預設行為。  
  
 在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，直接執行命令 (但不先準備命令) 時，系統會建立並快取執行計畫。 如果再次執行了 SQL 陳述式，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 就會具有高效率演算法，可比對新的陳述式與快取中的現有執行計畫，然後針對該陳述式重複使用此執行計畫。  
  
 若為準備的命令，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會針對準備和執行命令陳述式提供原生支援。 當您準備陳述式時，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會建立執行計畫、快取此計畫，並且將此執行計畫的控制代碼傳回給提供者。 然後，提供者會使用此控制代碼來重複執行陳述式。 此時，系統不會建立任何預存程序。 因為此控制代碼會直接識別 SQL 陳述式的執行計畫，而非比對陳述式與快取中的執行計畫 (如同直接執行的情況)，所以如果您知道陳述式將執行許多次，準備陳述式會比直接執行更有效率。  
  
 在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中，準備的陳述式無法用來建立暫存物件，而且無法參考建立暫存物件 (例如暫存資料表) 的系統預存程序。 這些程序必須直接執行。  
  
 您永遠都不應該準備某些命令。 例如，您不應該準備指定預存程序執行或針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預存程序建立包含無效文字的命令。  
  
 建立暫存預存程序時，如果 SQL Server OLE DB 驅動程式會執行暫存的預存程序，如同執行陳述式本身傳回的結果。  
  
 建立暫存預存程序由 OLE DB 驅動程式所控制的 SQL Server-特有的初始化屬性 SSPROP_INIT_USEPROCFORPREP。 如果屬性值為 SSPROPVAL_USEPROCFORPREP_ON 或 SSPROPVAL_USEPROCFORPREP_ON_DROP，SQL Server OLE DB 驅動程式會嘗試建立預存程序，準備命令時。 如果應用程式使用者具有足夠的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 權限，預存程序建立就會成功。  
  
 不常中斷連接的取用者，建立暫存預存程序可能需要大量資源的**tempdb**、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]建立暫存物件的系統資料庫。 如果 SSPROP_INIT_USEPROCFORPREP 的值為 SSPROPVAL_USEPROCFORPREP_ ON，當建立命令的工作階段失去的執行個體的連接時，才，會卸除暫存預存程序適用於SQLServerOLEDB驅動程式所建立[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. 如果該連接是針對資料來源初始化所建立的預設連接，只有當資料來源成為未初始化時，才會卸除暫存預存程序。  
  
 如果 SSPROP_INIT_USEPROCFORPREP 的值為 SSPROPVAL_USEPROCFORPREP_ON_DROP，當發生下列其中一項時，會卸除的 OLE DB Driver for SQL Server 暫存預存程序：  
  
-   取用者使用**icommandtext:: Setcommandtext**表示新的命令。  
  
-   取用者使用**icommandprepare:: Unprepare**來指出它不再需要命令文字。  
  
-   取用者使用暫存預存程序來釋放命令物件的所有參考。  
  
 在命令物件具有最多一個暫存預存程序**tempdb**。 任何現有的暫存預存程序都代表特定命令物件的目前命令文字。  
  
## <a name="see-also"></a>另請參閱  
 [命令](../../oledb/ole-db-commands/commands.md)  
  
  
