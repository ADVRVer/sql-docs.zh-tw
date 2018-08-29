---
title: sp_addlinkedsrvlogin & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_addlinkedsrvlogin_TSQL
- sp_addlinkedsrvlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addlinkedsrvlogin
ms.assetid: eb69f303-1adf-4602-b6ab-f62e028ed9f6
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6f9afac01a491031a31a8fc96022d391bdb75659
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43035993"
---
# <a name="spaddlinkedsrvlogin-transact-sql"></a>sp_addlinkedsrvlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  建立或更新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本機執行個體登入與遠端伺服器安全性帳戶之間的對應。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_addlinkedsrvlogin [ @rmtsrvname = ] 'rmtsrvname'   
     [ , [ @useself = ] 'TRUE' | 'FALSE' | NULL ]   
     [ , [ @locallogin = ] 'locallogin' ]   
     [ , [ @rmtuser = ] 'rmtuser' ]   
     [ , [ @rmtpassword = ] 'rmtpassword' ]   
```  
  
## <a name="arguments"></a>引數  
 [ @rmtsrvname **=** ] **'***rmtsrvname***'**  
 這是登入對應所套用的連結伺服器名稱。 *rmtsrvname&lt*已**sysname**，沒有預設值。  
  
 [ @useself **=** ] **'** TRUE **'** | 'FALSE' | 'NULL'  
 決定是否連接到*rmtsrvname&lt*模擬本機登入或明確提交登入和密碼。 資料類型是**varchar (** 8 **)**，預設值是 TRUE。  
  
 值為 TRUE 可讓您指定登入使用他們自己的認證來連接到*rmtsrvname&lt*，使用*rmtuser&lt*並*rmtpassword&lt*引數被忽略。 FALSE 指定*rmtuser&lt*並*rmtpassword&lt*引數用來連接到*rmtsrvname&lt*指定*locallogin*. 如果*rmtuser&lt*並*rmtpassword&lt*也會設為 NULL、 沒有登入或密碼用來連接到連結的伺服器。  
  
 [ @locallogin **=** ] **'***locallogin***'**  
 這是本機伺服器上的登入。 *locallogin*已**sysname**，預設值是 NULL。 NULL 可讓您指定這個項目會套用到所有的本機登入，連接到*rmtsrvname&lt*。 如果不是 NULL， *locallogin*可以是[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]登入或 Windows 登入。 必須以直接方式或透過其被授與存取權限之 Windows 群組的成員資格，來授與 Windows 登入存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的權限。  
  
 [ @rmtuser **=** ] **'***rmtuser&lt***'**  
 用來連接到遠端登入*rmtsrvname&lt*當@useself為 FALSE。 遠端伺服器時的執行個體[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]不使用 Windows 驗證*rmtuser&lt*是[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]登入。 *rmtuser&lt*已**sysname**，預設值是 NULL。  
  
 [ @rmtpassword **=** ] **'***rmtpassword&lt***'**  
 密碼相關聯*rmtuser&lt*。 *rmtpassword&lt*已**sysname**，預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>備註  
 當使用者登入本機伺服器並執行存取連結伺服器資料表的分散式查詢時，本機伺服器必須代表使用者登入連結伺服器來存取該資料表。 使用 sp_addlinkedsrvlogin 來指定本機伺服器用來登入連結伺服器的登入認證。  
  
> [!NOTE]  
>  若要在連結的伺服器上使用資料表時建立最佳查詢計畫，查詢處理器必須具有連結伺服器的資料分佈統計資料。 對於資料表之任何資料行擁有受限權限的使用者可能沒有足夠的權限來取得所有有用的統計資料，而且可能會收到效率較低的查詢計畫並遇到效能不佳的情況。 如果連結的伺服器是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，則使用者必須擁有資料表，或者使用者必須是連結伺服器之系統管理員 (sysadmin) 固定伺服器角色、db_owner 固定資料庫角色或 db_ddladmin 固定資料庫角色的成員，才能取得所有可用的統計資料。 SQL Server 2012 SP1 會修改取得統計資料的權限限制，以及允許具有 SELECT 權限的使用者存取可透過 DBCC SHOW_STATISTICS 提供的統計資料。 如需詳細資訊，請參閱下的 [權限] 區段[DBCC SHOW_STATISTICS &#40;TRANSACT-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)。  
  
 藉由執行 sp_addlinkedserver，自動在本機伺服器的所有登入及連結伺服器的遠端登入之間建立預設對應。 預設對應指出代表登入連接至連結伺服器時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會使用本機登入的使用者認證。 這相當於執行使用 sp_addlinkedsrvlogin@useself設定為 **，則為 true**連結的伺服器，而不指定本機使用者名稱。 sp_addlinkedsrvlogin 僅適用於變更預設對應或新增特定本機登入的對應。 若要刪除預設對應或任何其他對應，請使用 sp_droplinkedsrvlogin。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 並不需要使用 sp_addlinkedsrvlogin 來建立預定的登入對應，而是在下列所有條件都存在時，可以自動利用發出查詢之使用者的 Windows 安全性認證 (Windows 使用者名稱及密碼) 來連接至連結伺服器：  
  
-   使用者利用 Windows 驗證模式連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
-   用戶端及傳送伺服器具有安全性帳戶委派。  
  
-   提供者支援 Windows 驗證模式；例如，在 Windows 執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
> [!NOTE]  
>  不需要為單躍點狀況啟用委派，但是多躍點狀況則必須啟用委派。  
  
 在連結伺服器利用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本機執行個體執行 sp_addlinkedsrvlogin 所定義的對應來執行驗證之後，遠端資料庫的個別物件權限是由連結伺服器所決定，而非本機伺服器。  
  
 sp_addlinkedsrvlogin 無法在使用者自訂交易內執行。  
  
## <a name="permissions"></a>Permissions  
 需要伺服器的 ALTER ANY LOGIN 權限。  
  
## <a name="examples"></a>範例  
  
### <a name="a-connecting-all-local-logins-to-the-linked-server-by-using-their-own-user-credentials"></a>A. 利用本身的使用者認證將所有本機登入連接至連結伺服器  
 下列範例建立對應來確保所有本機伺服器的登入，是利用本身的使用者認證來連接至連結伺服器 `Accounts`。  
  
```  
EXEC sp_addlinkedsrvlogin 'Accounts';  
```  
  
 或  
  
```  
EXEC sp_addlinkedsrvlogin 'Accounts', 'true';  
```  
  
> [!NOTE]  
>  如果有為個別登入建立的明確對應，這些對應優先於該連結伺服器可能存在的任何全域對應。  
  
### <a name="b-connecting-a-specific-login-to-the-linked-server-by-using-different-user-credentials"></a>B. 使用不同的使用者認證，將特定的登入連接到連結伺服器  
 下列範例會建立對應，以確保 Windows 使用者 `Domain\Mary` 利用登入 `Accounts` 和密碼 `MaryP`，連接至連結伺服器 `d89q3w4u`。  
  
```  
EXEC sp_addlinkedsrvlogin 'Accounts', 'false', 'Domain\Mary', 'MaryP', 'd89q3w4u';  
```  
  
> [!IMPORTANT]  
>  這個範例不使用 Windows 驗證。 密碼會以未經加密的方式傳輸。 在儲存於磁碟的資料來源定義和指令碼中、備份中和記錄檔中，可能看得見密碼。 請勿在這種連接中使用管理員密碼。 如需您環境的特定安全性指引，請洽詢網路管理員。  
  
## <a name="see-also"></a>另請參閱  
 [連結的伺服器目錄檢視&#40;Transact SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_droplinkedsrvlogin &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
