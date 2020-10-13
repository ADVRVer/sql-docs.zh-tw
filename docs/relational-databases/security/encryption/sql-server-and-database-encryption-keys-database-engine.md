---
title: SQL Server 與資料庫加密金鑰
description: 了解 SQL Server 資料庫引擎用來加密及保護資料的服務主要金鑰與資料庫主要金鑰。
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- keys [SQL Server], database encryption
ms.assetid: 15c0a5e8-9177-484c-ae75-8c552dc0dac0
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: c73439c6fd7015bcd6bbae61d4164348331deb17
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91866592"
---
# <a name="sql-server-and-database-encryption-keys-database-engine"></a>SQL Server 和資料庫加密金鑰 (Database Engine)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會使用加密金鑰來保護儲存於伺服器資料庫中之資料、認證和連接資訊的安全。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 有兩種類型的金鑰： *「對稱」* (Symmetric) 與 *「非對稱」* (Asymmetric)。 對稱金鑰會使用相同的密碼為資料加密與解密。 非對稱金鑰會使用某個密碼來加密資料 (稱為「公開」金鑰)，並使用另一個密碼來解密資料 (稱為「私密」金鑰)。  
  
 在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中，加密金鑰包括用於保護機密資料的公開、私密和對稱金鑰的組合。 當您初次啟動 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體時，會在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 初始化期間建立對稱金鑰。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會使用此金鑰來加密 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]內所儲存的敏感性資料。 公開金鑰和私密金鑰是由作業系統所建立，可用來保護對稱金鑰。 針對負責儲存資料庫中之敏感性資料的每一個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體，建立一組公開金鑰和私密金鑰。  
  
## <a name="applications-for-sql-server-and-database-keys"></a>SQL Server 和資料庫金鑰的套用  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 對於金鑰有兩個主要的應用：針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體產生「服務主要金鑰」(SMK)，並將「資料庫主要金鑰」(DMK) 用於資料庫。

### <a name="service-master-key"></a>服務主要金鑰
  
 服務主要金鑰是 SQL Server 加密階層的根。 SMK 會在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體第一次啟動時自動產生，且用以加密各資料庫的連結伺服器密碼、認證和資料庫主要金鑰。 SMK 是以本機電腦金鑰或 Windows 資料保護 API (DPAPI) 加密。 DPAPI 會使用一個衍生自 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務帳戶和電腦認證之 Windows 認證的金鑰。 服務主要金鑰只能由建立它時所使用的服務帳戶解密，或是只能由可以存取電腦認證的主體解密。

服務主要金鑰只能由建立此金鑰的 Windows 服務帳戶來開啟，或是由可存取服務帳戶名稱及其密碼的主體來開啟。

 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 是使用 AES 加密演算法來保護服務主要金鑰 (SMK) 及資料庫主要金鑰 (DMK)。 與舊版中使用的 3DES 相比，AES 是一種較新的加密演算法。 將 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 執行個體升級至 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 之後，應該會重新產生 SMK 和 DMK，以將主要金鑰升級至 AES。 如需重新產生 SMK 的詳細資訊，請參閱 [ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-service-master-key-transact-sql.md) 和 [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-master-key-transact-sql.md)。

### <a name="database-master-key"></a>資料庫主要金鑰
  
 資料庫主要金鑰是一個用來保護資料庫中憑證之私密金鑰和非對稱金鑰的對稱金鑰。 它也可以用來加密資料，但是有長度上的限制，因此與對稱金鑰相較之下，它用於資料時比較不實用。 若要啟用資料庫主要金鑰的自動解密，則需使用 SMK 來加密此金鑰的複本。 這個複本會同時存放在使用它的資料庫和 **master** 系統資料庫中。  
  
 每當 DMK 變更時，也會以無訊息模式更新儲存於 **master** 系統資料庫中的 DMK 複本。 但是，此預設值可以使用 **DROP ENCRYPTION BY SERVICE MASTER KEY** 陳述式的 **ALTER MASTER KEY** 選項來加以變更。 未以服務主要金鑰加密的 DMK 必須使用 **OPEN MASTER KEY** 陳述式和密碼來開啟。  
  
## <a name="managing-sql-server-and-database-keys"></a>管理 SQL Server 和資料庫金鑰  
 加密金鑰的管理包括建立新的資料庫金鑰、建立伺服器和資料庫金鑰的備份，以及了解還原、刪除或變更金鑰的時機和方法。  
  
 若要管理對稱金鑰，您可以使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 所包含的工具執行以下作業：  
  
-   備份伺服器和資料庫金鑰的複本，讓您能夠使用它們來復原伺服器安裝，或當做計劃移轉的一部分。  
  
-   將之前儲存的金鑰還原至資料庫。 如此可讓新的伺服器執行個體存取它原先未加密的現有資料。  
  
-   當發生無法再存取加密資料的罕見事件中，刪除資料庫中的加密資料。  
  
-   在金鑰受到危害的罕見事件中，重新建立金鑰並重新加密資料。 就安全性最佳作法而言，您應定期重新建立金鑰 (例如，每隔幾個月)，以保護伺服器免於駭客進行破解金鑰的攻擊。  
  
-   在伺服器向外延展部署中加入或移除伺服器執行個體，其中多部伺服器會共用單一資料庫以及能加解密該資料庫的金鑰。  
  
## <a name="important-security-information"></a>重要安全性資訊  
 存取由服務主要金鑰維護安全的物件需要之前用來建立此金鑰的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務帳戶或是電腦帳戶。 也就是說，電腦會與金鑰建立所在的系統繫結在一起。 您可以變更 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務帳戶 *或* 電腦帳戶，而不會遺失對此金鑰的存取權。 但是，如果您變更這兩者，您將會遺失對服務主要金鑰的存取權。 如果您在沒有這兩個元素之其中一個的情況下遺失對服務主要金鑰的存取權，您將無法使用原始金鑰來解密資料和物件。  
  
 以服務主要金鑰維護安全的連接一定要有服務主要金鑰，才能進行還原。  
  
 當存取以資料庫主要金鑰維護安全的物件和資料時，只需要用來維護此金鑰安全的密碼。  
  
> [!CAUTION]  
>  如果您遺失對上述金鑰的所有存取權，您也會遺失用這些金鑰維護安全之物件、連接和資料的存取權。 您可以還原服務主要金鑰 (如這裡所顯示的連結中所述)，或者回到原始加密系統來復原存取。 並沒有其他「捷徑」可復原存取。  
  
## <a name="in-this-section"></a>本節內容  
 [服務主要金鑰]()  
 提供服務主要金鑰和其最佳作法的簡短說明。  
  
 [可延伸金鑰管理 &#40;EKM&#41;](../../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
 說明如何搭配 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]使用協力廠商金鑰管理系統。  
  
## <a name="related-tasks"></a>相關工作  
 [備份服務主要金鑰](../../../relational-databases/security/encryption/back-up-the-service-master-key.md)  
  
 [還原服務主要金鑰](../../../relational-databases/security/encryption/restore-the-service-master-key.md)  
  
 [建立資料庫主要金鑰](../../../relational-databases/security/encryption/create-a-database-master-key.md)  
  
 [備份資料庫主要金鑰](../../../relational-databases/security/encryption/back-up-a-database-master-key.md)  
  
 [還原資料庫主要金鑰](../../../relational-databases/security/encryption/restore-a-database-master-key.md)  
  
 [在兩部伺服器上建立相同的對稱金鑰](../../../relational-databases/security/encryption/create-identical-symmetric-keys-on-two-servers.md)  
  
 [使用 EKM 在 SQL Server 上啟用 TDE](../../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)  
  
 [使用 Azure 金鑰保存庫進行可延伸金鑰管理 &#40;SQL Server&#41;](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
 [加密資料行](../../../relational-databases/security/encryption/encrypt-a-column-of-data.md)  
  
## <a name="related-content"></a>相關內容  
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-master-key-transact-sql.md)  
  
 [ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-service-master-key-transact-sql.md)  
  
 [還原資料庫主要金鑰](../../../relational-databases/security/encryption/restore-a-database-master-key.md)  
  
## <a name="see-also"></a>另請參閱  
 [備份與還原 Reporting Services 加密金鑰](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)   
 [刪除和重新建立加密金鑰 &#40;SSRS 組態管理員&#41;](../../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)   
 [加入和移除向外延展部署的加密金鑰 &#40;SSRS 組態管理員&#41;](../../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md)   
 [透明資料加密 &#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
