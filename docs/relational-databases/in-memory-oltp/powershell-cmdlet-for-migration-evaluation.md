---
title: 用於移轉評估的 PowerShell Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 117250d3-9982-47fe-94fd-6f29f6159940
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9fb4f3fccb28f2210354eb4cc1a6828deaa6cbb7
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43069441"
---
# <a name="powershell-cmdlet-for-migration-evaluation"></a>用於移轉評估的 PowerShell Cmdlet
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Save-SqlMigrationReport Cmdlet 是一種工具，可評估 SQL Server 資料庫中多個物件的移轉適用性。 目前，它僅限於評估記憶體內部 OLTP 的移轉適用性。 您可在提高權限的 Windows PowerShell 環境和 sqlps 中執行此 Cmdlet。  
  
## <a name="syntax"></a>語法  
  
```powershell  
Save-SqlMigrationReport [ -MigrationType OLTP ] [ -Server server -Database database [ -Object object_name ] ]  |  [ -InputObject smo_object ] -FolderPath path  
```  
  
#### <a name="parameters"></a>參數  
 下表將說明這些參數。  
  
|參數|Description|  
|----------------|-----------------|  
|MigrationType|Cmdlet 的目標移轉案例類型。 目前唯一的值是預設 OLTP。 選擇性。|  
|[伺服器]|目標 SQL Server 執行個體的名稱。 如果未提供 -InputObject 參數，則為 Windows Powershell 環境中的必要項。 在 SQLPS 中為選擇性參數。|  
|[資料庫]|目標 SQL Server 資料庫的名稱。 如果未提供 -InputObject 參數，則為 Windows Powershell 環境中的必要項。 在 SQLPS 中為選擇性參數。|  
|Object|目標資料庫物件的名稱。 可以是資料表或預存程序。|  
|InputObject|Cmdlet 的目標 SMO 物件。 如果未提供 -Server 和 -Database，則為 Windows Powershell 環境中的必要項。 在 SQLPS 中為選擇性參數。|  
|FolderPath|Cmdlet 用於儲放所產生報表的資料夾。 必要。|  
  
## <a name="results"></a>結果  
 -FolderPath 參數中指定的資料夾，其中會有「資料表」和「預存程序」這兩個資料夾名稱。 如果目標的物件是資料表，它的報表就會在「資料表」資料夾內。 否則，就會在「預存程序」資料夾內。  
  
  
