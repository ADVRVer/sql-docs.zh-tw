---
title: sp_addserver (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addserver
- sp_addserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addserver
- renaming servers
- machine names [SQL Server]
- computer names
ms.assetid: 160a6b29-5e80-44ab-80ec-77d4280f627c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 616b835b2b190346df4891caa4d7295c8fb328e1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022427"
---
# <a name="spaddserver-transact-sql"></a>sp_addserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]定義  本機執行個體的名稱。 當電腦裝載[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]是重新命名，使用**sp_addserver**通知的執行個體[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]了新的電腦名稱。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 此程序必須在電腦上裝載的所有  執行個體上執行。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 無法變更  的執行個體名稱。 若要變更具名執行個體的執行個體名稱，請安裝具有所需名稱的新執行個體、從舊的執行個體卸離資料庫檔案、將資料庫附加到新的執行個體，和卸除舊的執行個體。 或者，您可以在用戶端電腦上建立用戶端別名名稱，將連接重新導向至不同的伺服器和執行個體名稱或 **伺服器：連接埠** 的組合，而不需要變更伺服器電腦上的執行個體名稱。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_addserver [ @server = ] 'server' ,  
     [ @local = ] 'local'   
     [ , [ @duplicate_ok = ] 'duplicate_OK' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @server = ] 'server'` 是伺服器的名稱。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 伺服器名稱必須是唯一，並且遵照  Windows 電腦名稱的規則 (但不能加空格)。 *server* 是 **sysname**，沒有預設值。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 當您在一部電腦安裝多個  執行個體時，每一個執行個體的運作方式，就好像分別位於不同的伺服器上。 藉由參考指定的具名執行個體*伺服器*作為*servername\instancename*。  
  
`[ @local = ] 'LOCAL'` 指定要新增為本機伺服器的伺服器。 **@local** 已**varchar(10)** ，預設值是 NULL。 指定 **@local** 作為**本機**定義 **@server** 原因與本機伺服器的名稱為 @@SERVERNAME傳回值的函式*server*。  
  
 在安裝時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式會將這個變數設為電腦名稱。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 依預設，電腦名稱是使用者在不用其他組態的情況下，連接  執行個體的方法。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 本機定義在  重新啟動之後才會生效。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]每個  執行個體只能定義一部本機伺服器。  
  
`[ @duplicate_ok = ] 'duplicate_OK'` 指定是否允許重複的伺服器名稱。 **@duplicate_OK** 已**varchar(13)** ，預設值是 NULL。 **@duplicate_OK** 只能有值**duplicate_OK**或 NULL。 如果**duplicate_OK**指定並已新增的伺服器名稱存在，不會引發錯誤。 如果沒有使用具名的參數，就 **@local** 必須指定。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>備註  
 若要設定或清除伺服器選項，請使用**sp_serveroption**。  
  
 **sp_addserver**無法用於使用者定義交易內。  
  
 使用**sp_addserver**新增遠端伺服器已停止。 請改用 [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) 。  
  
## <a name="permissions"></a>Permissions  
  需要 setupadmin 固定伺服器角色中的成員資格。  
  
## <a name="examples"></a>範例  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 下列範例將裝載 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之電腦名稱的 `ACCOUNTS`項目變更為 。  
  
```  
sp_addserver 'ACCOUNTS', 'local';  
```  
  
## <a name="see-also"></a>另請參閱  
 [重新命名主控 SQL Server 的獨立執行個體的電腦](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_dropserver &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [安全性預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  
