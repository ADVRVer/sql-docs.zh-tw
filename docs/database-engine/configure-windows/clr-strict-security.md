---
title: "CLR 嚴格安全性 | Microsoft Docs"
description: "如何設定 SQL Server 中的 CLR 嚴格安全性"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- clr strict security
- clr_strict_security_TSQL
- clr strict security
- strict_security_TSQL
helpviewer_keywords:
- assemblies [CLR integration], strick security
- clr strict security option
ms.assetid: 
caps.latest.revision: 0
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 54f976fac931d9cdc731f4b3e91c433d66310194
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="clr-strict-security"></a>CLR 嚴格安全性   
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

控制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中 `SAFE`、`EXTERNAL ACCESS`、`UNSAFE` 權限的解譯。   

|值 |描述 | 
|----- |----- | 
|0 |Disabled - 針對回溯相容性所提供。 不建議使用 `Disabled` 值。 | 
|1 |Enabled - 讓 [!INCLUDE[ssde-md](../../includes/ssde-md.md)] 忽略組件的 `PERMISSION_SET` 資訊，而且一律會將它們解釋為 `UNSAFE`。  `Enabled` 是 [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] 的預設值。 | 

>  [!WARNING]
>  CLR 使用 .NET Framework 中的程式碼存取安全性 (CAS)，而這不再支援為安全性界限。 使用 `PERMISSION_SET = SAFE` 所建立的 CLR 組件可能可以存取外部系統資源、呼叫 Unmanaged 程式碼，以及需要 sysadmin 權限。 從 [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] 開始，引進稱為 `clr strict security` 的 `sp_configure` 選項，來增強 CLR 組件的安全性。 `clr strict security` 預設會予以啟用，並將 `SAFE` 和 `EXTERNAL_ACCESS` 組件視為就像標示上 `UNSAFE` 一樣。 可以基於回溯相容性停用 `clr strict security` 選項，但不建議這麼做。 Microsoft 建議透過具有已獲授與 master 資料庫中 `UNSAFE ASSEMBLY` 權限之對應登入的憑證或非對稱金鑰簽署所有組件。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員也可以將組件新增至資料庫引擎應該信任的組件清單。 如需詳細資訊，請參閱 [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md)。

## <a name="remarks"></a>備註   

啟用時，會在執行階段忽略 `CREATE ASSEMBLY` 和 `ALTER ASSEMBLY` 陳述式中的 `PERMISSION_SET` 選項，但在中繼資料中會保留 `PERMISSION_SET` 選項。 忽略此選項可將中斷現有程式碼陳述式最小化。

`CLR strict security` 是 `advanced option`。  

>  [!IMPORTANT]  
>  啟用嚴格安全性之後，將無法載入任何未簽署的組件。 您必須改變或置放並重新建立每個組件，以使用憑證或非對稱金鑰進行簽署，該金鑰有具有伺服器 `UNSAFE ASSEMBLY` 權限的對應登入。

## <a name="permissions"></a>Permissions 

### <a name="to-change-this-option"></a>變更此選項  
需要 `CONTROL SERVER` 權限或系統管理員 `sysadmin` 固定伺服器角色中的成員資格。

### <a name="to-create-an-clr-assembly"></a>建立 CLR 組件   
啟用 `CLR strict security` 時，需要有下列權限才能建立 CLR 組件：

- 使用者必須具有 `CREATE ASSEMBLY` 權限  
- 而且，下列其中一個條件也必須成立：  
  - 組件是使用憑證或非對稱金鑰進行簽署，該金鑰有具有伺服器 `UNSAFE ASSEMBLY` 權限的對應登入。 建議簽署組件。  
  - 資料庫的 `TRUSTWORTHY` 屬性設定為 `ON`，而且具有伺服器之 `UNSAFE ASSEMBLY` 權限的登入擁有資料庫。 不建議使用此選項。  

  
## <a name="see-also"></a>另請參閱  
  
 [伺服器組態選項 &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [CLR 已啟用伺服器組態選項](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)

