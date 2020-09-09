---
description: sp_helpmergesubscription (Transact-SQL)
title: sp_helpmergesubscription (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergesubscription
- sp_helpmergesubscription_TSQL
helpviewer_keywords:
- sp_helpmergesubscription
ms.assetid: da564112-f769-4e67-9251-5699823e8c86
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 48d40b3209311968443a6c6d2b713b4aa1e3d43a
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89535189"
---
# <a name="sp_helpmergesubscription-transact-sql"></a>sp_helpmergesubscription (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  將訂閱的相關資訊傳回合併式發行集，發送和提取訂閱都包括在內。 這個預存程序執行於發行集資料庫的發行者端，或訂閱資料庫的重新發行訂閱者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helpmergesubscription [ [ @publication=] 'publication']  
    [ , [ @subscriber=] 'subscriber']  
    [ , [ @subscriber_db=] 'subscriber_db']  
    [ , [ @publisher=] 'publisher']  
    [ , [ @publisher_db=] 'publisher_db']  
    [ , [ @subscription_type=] 'subscription_type']  
    [ , [ @found=] 'found' OUTPUT]  
```  
  
## <a name="arguments"></a>引數  
`[ @publication = ] 'publication'` 這是發行集的名稱。 *發行* 集是 **sysname**，預設值是 **%** 。 發行集必須已存在，且符合識別碼的規則。 如果為 Null 或 **%** ，則會傳回目前資料庫中所有合併式發行集和訂閱的相關資訊。  
  
`[ @subscriber = ] 'subscriber'` 這是訂閱者的名稱。 *訂閱者* 是 **sysname**，預設值是 **%** 。 如果是 NULL 或 %，就會傳回給定發行集之所有訂閱的相關資訊。  
  
`[ @subscriber_db = ] 'subscriber_db'` 這是訂閱資料庫的名稱。 *subscriber_db*是 **sysname**，預設值是 **%** ，它會傳回所有訂閱資料庫的相關資訊。  
  
`[ @publisher = ] 'publisher'` 這是發行者的名稱。 發行者必須是有效伺服器。 *publisher*是 **sysname**，預設值是 **%** ，它會傳回所有發行者的相關資訊。  
  
`[ @publisher_db = ] 'publisher_db'` 這是發行者資料庫的名稱。 *publisher_db*是 **sysname**，預設值是 **%** ，它會傳回所有發行者資料庫的相關資訊。  
  
`[ @subscription_type = ] 'subscription_type'` 這是訂閱的類型。 *subscription_type*是 **Nvarchar (15) **，它可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**推送** (預設) |發送訂閱|  
|**拉**|提取訂閱|  
|**對**|發送訂閱和提取訂閱|  
  
`[ @found = ] 'found'OUTPUT` 這是表示傳回資料列的旗標。 *找到* **int** 和 OUTPUT 參數，預設值是 Null。 **1** 表示找到發行集。 **0** 表示找不到發行集。  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**subscription_name**|**sysname**|訂閱的名稱。|  
|**出版**|**sysname**|發行集的名稱。|  
|**publisher**|**sysname**|發行者的名稱。|  
|**publisher_db**|**sysname**|發行者資料庫的名稱。|  
|**使用者**|**sysname**|訂閱者的名稱。|  
|**subscriber_db**|**sysname**|訂閱資料庫的名稱。|  
|**status**|**int**|訂閱的狀態：<br /><br /> **0** = 所有作業都在等待啟動<br /><br /> **1** = 一或多個作業正在啟動<br /><br /> **2** = 所有作業都已成功執行<br /><br /> **3** = 至少有一項工作正在執行<br /><br /> **4** = 所有作業都已排程和閒置<br /><br /> **5** = 至少有一項作業在先前的失敗之後嘗試執行<br /><br /> **6** = 至少有一項作業無法成功執行|  
|**subscriber_type**|**int**|訂閱者的類型。|  
|**subscription_type**|**int**|訂閱的類型：<br /><br /> **0** = 推送<br /><br /> **1** = 提取<br /><br /> **2** = 兩者|  
|**priority**|**float (8) **|表示訂閱優先權的數字。|  
|**sync_type**|**tinyint**|訂閱同步處理類型。|  
|**description**|**nvarchar(255)**|這項合併訂閱的簡要描述。|  
|**merge_jobid**|**binary(16)**|合併代理程式的作業識別碼。|  
|**full_publication**|**tinyint**|這是指訂閱完整或篩選發行集。|  
|**offload_enabled**|**bit**|指定是否已將複寫代理程式的卸載執行設成執行於訂閱者端。 如果是 NULL，就是執行於發行者端。|  
|**offload_server**|**sysname**|執行代理程式的伺服器名稱。|  
|**use_interactive_resolver**|**int**|傳回是否在重新調整期間使用互動式解析程式。 如果是 **0**，則不會使用互動式解析程式。|  
|**hostname**|**sysname**|當依據 [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) 函數的值篩選訂閱時，所提供的值。|  
|**subscriber_security_mode**|**smallint**|這是訂閱者端的安全性模式， **1** 表示 Windows 驗證， **0** 表示 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證。|  
|**subscriber_login**|**sysname**|這是在訂閱者端的登入名稱。|  
|**subscriber_password**|**sysname**|永遠不傳回實際的訂閱者密碼。 結果會以 " **\*\*\*\*\*\*** " 字串遮罩。|  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或 **1** (失敗)   
  
## <a name="remarks"></a>備註  
 **sp_helpmergesubscription** 用於合併式複寫中，以傳回儲存在「發行者」或「重新發行訂閱者」端的訂閱資訊。  
  
 若為匿名訂閱， *subscription_type*值一律為 **1** (提取) 。 不過，您必須在「訂閱者」端執行 [sp_helpmergepullsubscription](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md) ，以取得匿名訂閱的相關資訊。  
  
## <a name="permissions"></a>權限  
 只有 **系統管理員（sysadmin** ）固定伺服器角色的成員、 **db_owner** 固定資料庫角色，或訂閱所屬發行集的發行集存取清單可以 **sp_helpmergesubscription**執行。  
  
## <a name="see-also"></a>另請參閱  
 [sp_addmergesubscription &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
