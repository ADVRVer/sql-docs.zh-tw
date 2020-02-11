---
title: sp_repladdcolumn （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repladdcolumn_TSQL
- sp_repladdcolumn
helpviewer_keywords:
- sp_repladdcolumn
ms.assetid: d6220f9f-c738-4f9c-bcf8-419994e86c81
author: stevestein
ms.author: sstein
ms.openlocfilehash: 75c66d1077b111837197957cc845b690b794ea24
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771055"
---
# <a name="sp_repladdcolumn-transact-sql"></a>sp_repladdcolumn (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  將資料行加入已發行的現有資料表發行項中。 它可讓您將新資料行加入發行這份資料表的所有發行者中，或只將資料行加入發行這份資料表的特定發行集。 這個預存程序執行於發行集資料庫的發行者端。  
  
> [!IMPORTANT]
>  這個預存程序已被取代，支援它的目的是為了回溯相容性。 它應該只用于[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]發行者和[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]重新發行訂閱者。 這個程序不應該用於含有 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本中導入之資料類型的資料行。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_repladdcolumn [ @source_object = ] 'source_object', [ @column = ] 'column' ]  
    [ , [ @typetext = ] 'typetext' ]  
    [ , [ @publication_to_add = ] 'publication_to_add' ]  
    [ , [ @from_agent = ] from_agent ]  
    [ , [ @schema_change_script = ] 'schema_change_script' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>引數  
 [ @source_object =]'*source_object*'  
 這是包含要加入之新資料行的資料表發行項名稱。 *source_object*是**Nvarchar （358**），沒有預設值。  
  
 [ @column =]' 資料*行*'  
 這是複寫要加入之資料表中的資料行名稱。 資料*行*是**sysname**，沒有預設值。  
  
 [ @typetext =]'*typetext*'  
 這是要加入之資料行的定義。 *typetext*是**Nvarchar （3000）**，沒有預設值。 例如，如果正在加入資料行 order_filled，而且它是單一字元欄位，而非 Null，而且預設值是**N**，則 order_filled 會是資料*行*參數，而資料行的定義**CHAR （1） NOT Null 條件約束 constraint_name 預設的 ' N '** 則是*typetext*參數值。  
  
 [ @publication_to_add =]'*publication_to_add*'  
 這是新資料行要加入其中的發行集名稱。 *publication_to_add*是**Nvarchar （4000）**，預設值是**ALL**。 若為**all**，則包含此資料表的所有發行集都會受到影響。 如果指定了*publication_to_add* ，則只有這個發行集已加入新的資料行。  
  
 [ @from_agent = ]*from_agent*  
 預存程序是否由複寫代理程式執行。 *from_agent*是**int**，預設值是**0**，當複寫代理程式執行這個預存程式時，會使用**1**的值，而在其他情況下，應該使用預設值**0**。  
  
 [ @schema_change_script =]'*schema_change_script*'  
 指定用來修改系統產生之自訂預存程序的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指令碼的名稱和路徑。 *schema_change_script*是**Nvarchar （4000）**，預設值是 Null。 複寫可讓使用者自訂的自訂預存程序，取代異動複寫所用的一個或多個預設程序。 *schema_change_script*是在使用 sp_repladdcolumn 對複寫的資料表發行項進行架構變更之後執行，而且可用來執行下列其中一項動作：  
  
-   如果自動重新產生自訂預存程式， *schema_change_script*可以用來卸載這些自訂預存程式，並以支援新架構的使用者定義自訂預存程式來取代它們。  
  
-   如果未自動重新產生自訂預存程式， *schema_change_script*可以用來重新產生這些預存程式，或建立使用者定義的自訂預存程式。  
  
 [ @force_invalidate_snapshot = ]*force_invalidate_snapshot*  
 啟用或停用使快照集失效的能力。 *force_invalidate_snapshot*是**bit**，預設值是**1**。  
  
 **1**指定發行項的變更可能會導致快照集無效，如果是這種情況， **1**的值會提供新快照集的許可權。  
  
 **0**指定發行項的變更不會使快照集失效。  
  
 [ @force_reinit_subscription = ]*force_reinit_subscription*  
 啟用或停用重新初始化訂閱的能力。 *force_reinit_subscription*是**位**，預設值是**0**。  
  
 **0**指定發行項的變更不會使訂閱重新初始化。  
  
 **1**指定發行項的變更可能會使訂閱重新初始化，如果是這種情況， **1**值會提供將進行訂閱重新初始化的許可權。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="permissions"></a>權限  
 只有系統管理員 (sysadmin) 固定伺服器角色和 db_owner 固定資料庫角色的成員，才能夠執行 sp_repladdcolumn。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 複寫中已淘汰的功能](../../relational-databases/replication/deprecated-features-in-sql-server-replication.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
