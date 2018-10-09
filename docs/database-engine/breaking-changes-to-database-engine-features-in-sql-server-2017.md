---
title: SQL Server 2017 資料庫引擎功能的重大變更 | Microsoft Docs
description: SQL Server 2017 資料庫引擎功能的重大變更
ms.date: 04/19/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.custom: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- breaking changes 2017 [SQL Server]
ms.assetid: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 1146af0e323345a514dad5a587b3f239b439c4c5
ms.sourcegitcommit: 7d702a1d01ef72ad5e133846eff6b86ca2edaff1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48798536"
---
# <a name="breaking-changes-to-database-engine-features-in-includesssqlv14-mdincludessssqlv14-mdmd"></a>[!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)] 資料庫引擎功能的重大變更
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]


  本主題描述 [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)] 中的重大變更。 這些變更可能會中斷以舊版 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]為根據的應用程式、指令碼或功能。 當您升級時可能會遇到這些問題。  
  
## <a name="breaking-changes-in-includesssqlv14-mdincludessssqlv14-mdmdincludessdeincludesssde-mdmd"></a>[!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)] 的重大變更  
  
-  CLR 使用 .NET Framework 中的程式碼存取安全性 (CAS)，而這不再作為安全性界限受支援。 從 [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)] 開始，引進稱為 `clr strict security` 的 `sp_configure` 選項，來增強 CLR 組件的安全性。 預設啟用 clr strict security，並將 `SAFE` 和 `EXTERNAL_ACCESS` CLR 組件視同標示了 `UNSAFE`。 可以基於回溯相容性停用 `clr strict security` 選項，但不建議這麼做。 停用 `clr strict security` 時，使用 `PERMISSION_SET = SAFE` 所建立的 CLR 組件可能可以存取外部系統資源、呼叫 Unmanaged 程式碼，以及需要 **sysadmin** 權限。 啟用嚴格安全性之後，任何未簽署的組件都將無法載入。 此外，如果資料庫有 `SAFE` 或 `EXTERNAL_ACCESS` 組件，`RESTORE` 或 `ATTACH DATABASE` 陳述式可以完成，但可能無法載入組件。   
  若要載入組件，您必須改變或置放並重新建立每個組件，以便使用憑證或非對稱金鑰簽署，該金鑰有具有伺服器 `UNSAFE ASSEMBLY` 權限的對應登入。 如需詳細資訊，請參閱 [CLR 嚴格安全性](../database-engine/configure-windows/clr-strict-security.md)。 


  
## <a name="previous-versions"></a>先前版本  

-   [SQL Server 2016 中對於 Database Engine 的重大變更](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)  
  
-   [SQL Server 2014 中對於 Database Engine 的重大變更](breaking-changes-to-database-engine-features-in-sql-server-2016.md)  
  
-   [SQL Server 2012 中對於 Database Engine 的重大變更](breaking-changes-to-database-engine-features-in-sql-server-2016.md)  
  
-   [SQL Server 2008 中對於 Database Engine 的重大變更](breaking-changes-to-database-engine-features-in-sql-server-2016.md)  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 2016 中已被取代的 Database Engine 功能](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [SQL Server 2016 中已停止的 Database Engine 功能](../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [SQL Server Database Engine 回溯相容性](../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [ALTER DATABASE 相容性層級 &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  
