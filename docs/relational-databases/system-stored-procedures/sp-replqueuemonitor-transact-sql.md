---
title: sp_replqueuemonitor (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_replqueuemonitor
- sp_replqueuemonitor_TSQL
helpviewer_keywords:
- sp_replqueuemonitor
ms.assetid: 6909a3f1-43a2-4df5-a6a5-9e6f347ac841
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 8c1d4737d5f1502d98a58f268b58c93cf71d71ab
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32998706"
---
# <a name="spreplqueuemonitor-transact-sql"></a>sp_replqueuemonitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  列出的佇列訊息[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]佇列或[!INCLUDE[msCoName](../../includes/msconame-md.md)]訊息佇列指定的發行集的佇列更新訂閱。 如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 佇列，這個預存程序便執行於訂閱資料庫的訂閱者端。 如果使用 Message Queuing，這個預存程序便執行於散發資料庫的散發者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_replqueuemonitor [ @publisher = ] 'publisher'  
    [ , [ @publisherdb = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @tranid = ] 'tranid' ]  
    [ , [ @queuetype = ] 'queuetype' ]  
```  
  
## <a name="arguments"></a>引數  
 [ **@publisher** = ] **'***publisher***'**  
 這是發行者的名稱。 *發行者*是**sysname**，預設值是 NULL。 必須設定伺服器的發行作業。 所有發行者都是 NULL。  
  
 [ **@publisherdb** =] **'***publisher_db***'** ]  
 這是發行集資料庫的名稱。 *publisher_db*是**sysname**，預設值是 NULL。 所有發行集資料庫都是 NULL。  
  
 [ **@publication** =] **'***發行集***'** ]  
 這是發行集的名稱。 *發行集*是**sysname**，預設值是 NULL。 所有發行集都是 NULL。  
  
 [ **@tranid** =] **'***tranid***'** ]  
 這是交易識別碼。 *tranid*是**sysname**，預設值是 NULL。 所有交易都是 NULL。  
  
 [**@queuetype=** ] **'***queuetype***'** ]  
 這是儲存交易的佇列類型。 *queuetype*是**tinyint**預設值是**0**，而且可以是下列值之一。  
  
|Value|描述|  
|-----------|-----------------|  
|**0**|所有佇列類型|  
|**1**|訊息佇列|  
|**2**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 佇列|  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_replqueuemonitor**用於快照式複寫或具有佇列更新訂閱的異動複寫中。 不會顯示不包含 SQL 命令的佇列訊息，或本身是跨越 SQL 命令之一部分的佇列訊息。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色或**db_owner**固定的資料庫角色可以執行**sp_replqueuemonitor**。  
  
## <a name="see-also"></a>另請參閱  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
