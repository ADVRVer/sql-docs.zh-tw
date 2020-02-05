---
title: TRUSTWORTHY 資料庫屬性 | Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database property
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ec745810697b325b8f1e1b2d5e67871136b9f089
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "68126815"
---
# <a name="trustworthy-database-property"></a>TRUSTWORTHY 資料庫屬性
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  TRUSTWORTHY 資料庫屬性是用來指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體是否信任資料庫及其中的內容。 依預設，此設定為 OFF，但可使用 ALTER DATABASE 陳述式來將它設為 ON。 例如： `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;` 。  
  
> [!NOTE]  
>  您必須是 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能設定此選項。  
  
 此屬性可用來減少因附加含有下列任一物件之資料庫而帶來的威脅：  
  
-   含有 EXTERNAL_ACCESS 或 UNSAFE 權限設定的惡意組件。 如需相關資訊，請參閱 [CLR Integration Security](../../relational-databases/clr-integration/security/clr-integration-security.md)。  
  
-   定義為以高階權限使用者身分來執行的惡意模組。 如需詳細資訊，請參閱 [EXECUTE AS 子句 &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md)。  
  
 這兩種情況都需要有特定程度的權限，而且在已附加至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的資料庫內容中使用時，都會受到適當的機制保護。 然而，如果資料庫離線了，具有資料庫檔案存取權的使用者可能會將其附加至所選取的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，並將具有惡意的內容加入資料庫。 當在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中卸離和附加資料庫時，會對資料和記錄檔設定某些權限，以限制對資料庫檔案的存取權。  
  
 因為附加至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的資料庫無法馬上獲得信任，所以該資料庫在被明確地標示為值得信任之前，將無法存取資料庫範圍以外的資源。 因此，若您備份或中斷連結已開啟 TRUSTWORTHY 選項的資料庫，且您將資料庫附加或還原到相同或另一個 SQL Server 執行個體，則會在附加/還原完成時關閉 TRUSTWORTHY 屬性。 此外，專為存取資料庫外部資源而設計的模組，以及具有 EXTERNAL_ACCESS 和 UNSAFE 權限設定的組件，都有額外的必備條件，才能順利地執行。  
  
## <a name="related-content"></a>相關內容  
 [SQL Server Database Engine 和 Azure SQL Database 的資訊安全中心](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
  
