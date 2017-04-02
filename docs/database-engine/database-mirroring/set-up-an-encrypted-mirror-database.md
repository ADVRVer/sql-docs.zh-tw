---
title: "設定加密鏡像資料庫 | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "密碼編譯 [SQL Server], 資料庫鏡像"
  - "加密 [SQL Server], 資料庫鏡像"
  - "資料庫主要金鑰 [SQL Server], 資料庫鏡像"
  - "鏡像資料庫 [SQL Server]"
  - "資料庫鏡像 [SQL Server], 安全性"
ms.assetid: 7329a575-be29-46e0-abc6-1344db37920c
caps.latest.revision: 24
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 24
---
# 設定加密鏡像資料庫
  若要啟用鏡像資料庫之資料庫主要金鑰的自動解密，則必須將用來加密主要金鑰的密碼提供給鏡像伺服器執行個體。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本包含傳送密碼的機制。 啟動資料庫鏡像之前，請先使用 **sp_control_dbmasterkey_password** 來建立資料庫主要金鑰的認證。 您必須為每個要進行鏡像的資料庫重複此程序。 如需詳細資訊，請參閱 [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)。  
  
> [!CAUTION]  
>  對於不想讓 **sa** 和其他具備高度權限的伺服器主體存取的資料庫，請不要啟用容錯移轉解密。 您可以將資料庫設為不能由服務主要金鑰解密它的金鑰階層。 此選項為資料庫提供深度的保護，該資料庫含有 **sa** 和其他具備高度權限的伺服器主體不應存取的資訊。 啟用此種資料庫的容錯移轉解密會移除此深度的保護，讓 **sa** 和其他具備高度權限的伺服器主體可解密資料庫。  
  
## 另請參閱  
 [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)   
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md)   
 [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md)   
 [加密階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [設定資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md)  
  
  