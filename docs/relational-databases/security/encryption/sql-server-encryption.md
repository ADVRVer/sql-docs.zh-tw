---
title: "SQL Server 加密 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "05/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "加密 [SQL Server], 關於加密"
  - "安全性 [SQL Server], 加密"
  - "加密 [SQL Server], 關於加密"
ms.assetid: ead0150e-4943-4ad5-84c8-36f85c7278f4
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# SQL Server 加密
  加密是透過金鑰或密碼的使用讓資料模糊化的程序。 這樣可以讓資料變成毫無用處，而不需要對應的解密金鑰或密碼。 加密並不能解決存取控制問題。 但是，若發生存取控制失靈的情形，加密可限縮資料遺失的風險以增強安全性。 例如，只要資料已加密，即使資料庫主機電腦設定不當而遭駭客取得敏感性資料，失竊的資訊就可能毫無用處。  
  
 您可以在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中針對連接、資料和預存程序使用加密。 下表包含 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中加密的詳細資訊。  
  
> [!IMPORTANT]  
>  雖然加密是維護安全性的寶貴工具，但是不應該將它用於所有的資料或連接。 當您決定是否要實作加密時，請考慮使用者將如何存取資料。 如果使用者透過公用網路存取資料，可能需要資料加密來提高安全性。 但是，如果所有的存取都與安全的內部網路組態有關，則可能不需要加密。 每次使用加密時，都應該包含密碼、金鑰和憑證的維護策略。  
  
> [!NOTE]  
>  傳輸層安全性 (TSL1.2) 的最新相關資訊位於 [Microsoft SQL Server 的 TLS 1.2 支援](https://support.microsoft.com/kb/3135244)。  
  
## 本節內容  
 [加密階層](../../../relational-databases/security/encryption/encryption-hierarchy.md)  
 有關 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中加密階層的資訊。  
  
 [選擇加密演算法](../../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
 有關如何選取有效加密演算法的詳細資訊。  
  
 [透明資料加密 &#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption-tde.md)  
 有關如何以透明方式加密資料的一般資訊。  
  
 [SQL Server 和資料庫加密金鑰 &#40;Database Engine&#41;](../../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)  
 在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，加密金鑰包括用於保護機密資料的公開、私密和對稱金鑰的組合。 本節將說明如何實作及管理加密金鑰。  
  
 [永遠加密 &#40;Database Engine&#41;](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
 確保以下人員無法存取加密資料：內部部署資料庫系統管理員、雲端資料庫操作員，或其他具備高權限但未經授權的使用者。  
  
 [動態資料遮罩](../../../relational-databases/security/dynamic-data-masking.md)  
 對不具權限的使用者遮罩敏感性資料，以限制其曝光。  
  
 [SQL Server 憑證與非對稱金鑰](../../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md)  
 使用公開金鑰加密的相關資訊。  
  
## 相關內容  
 [保護 SQL Server 的安全](../../../relational-databases/security/securing-sql-server.md)  
 如何有助於維護 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 平台安全及如何處理使用者與安全性物件的概觀。  
  
 [密碼編譯函數 &#40;Transact-SQL&#41;](../../../t-sql/functions/cryptographic-functions-transact-sql.md)  
 有關如何實作密碼編譯函數的資訊。  
  
 [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](../../../t-sql/functions/encryptbypassphrase-transact-sql.md)  
 有關如何使用密碼來加密資料的資訊。  
  
 [ENCRYPTBYKEY &#40;Transact-SQL&#41;](../../../t-sql/functions/encryptbykey-transact-sql.md)  
 有關如何使用對稱金鑰來加密資料的資訊。  
  
 [ENCRYPTBYASYMKEY &#40;Transact-SQL&#41;](../../../t-sql/functions/encryptbyasymkey-transact-sql.md)  
 有關如何使用非對稱金鑰來加密資料的資訊。  
  
 [ENCRYPTBYCERT &#40;Transact-SQL&#41;](../../../t-sql/functions/encryptbycert-transact-sql.md)  
 有關如何使用憑證來加密資料的資訊。  
  
## 外部資源  
 [Microsoft TechNet：SQL Server TechCenter：SQL Server 2005 安全性和保護](https://msdn.microsoft.com/sqlserver/bb895847.aspx)  
 有關 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安全性的最新資訊。  
  
## 另請參閱  
 [sys.key_encryptions &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-key-encryptions-transact-sql.md)   
 [SQL Server 和資料庫加密金鑰 &#40;Database Engine&#41;](../../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [備份與還原 Reporting Services 加密金鑰](../../../reporting-services/install-windows/back-up-and-restore-reporting-services-encryption-keys.md)  
  
  