---
description: sp_helpreplicationdboption (Transact-SQL)
title: sp_helpreplicationdboption (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpreplicationdboption_TSQL
- sp_helpreplicationdboption
helpviewer_keywords:
- sp_helpreplicationdboption
ms.assetid: 143ce689-108b-49d7-9892-fd3a86897f38
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6733b1f473c91094bd8af177bce4b13f3cf1b03e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89526895"
---
# <a name="sp_helpreplicationdboption-transact-sql"></a>sp_helpreplicationdboption (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  顯示發行者端的資料庫是否啟用複寫。 這個預存程序執行於任何資料庫的發行者端。 *不支援 Oracle 發行者使用這個值。*  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helpreplicationdboption [ [ @dbname =] 'dbname' ]  
    [ , [ @type = ] 'type' ]  
    [ , [ @reserved = ] reserved ]  
```  
  
## <a name="arguments"></a>引數  
`[ @dbname = ] 'dbname'` 這是資料庫的名稱。 *dbname* 是 **sysname**，預設值是 **%** 。 如果為 **%** ，則結果集會包含「發行者」端的所有資料庫，否則只會傳回指定資料庫的資訊。 如下所描述，使用者沒有適當權限的任何資料庫都不會傳回資訊。  
  
`[ @type = ] 'type'` 限制結果集只包含已啟用指定複寫選項 *類型* 值的資料庫。 *type* 是 **sysname**，它可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**發佈**|允許異動複寫。|  
|**合併發行**|允許合併式複寫。|  
|**允許** 複寫 (預設) |允許交易式或合併式複寫。|  
  
`[ @reserved = ] reserved` 指定是否傳回現有發行集和訂閱的資訊。 *reserved* 是 **bit**，預設值是0。 如果是 **1**，結果集會包含有關指定的資料庫是否有任何現有發行集或訂閱的資訊。  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|資料庫的名稱。|  
|**id**|**int**|資料庫識別碼。|  
|**transpublish**|**bit**|如果已針對快照式或交易式發行啟用資料庫，值為 **1** 時，表示已啟用快照集或交易式發行。|  
|**mergepublish**|**bit**|如果已針對合併發行啟用資料庫，值為 **1** 表示已啟用合併式發行。|  
|**dbowner**|**bit**|如果使用者是 **db_owner** 固定資料庫角色的成員，則為，值為 **1** 時，表示使用者是此角色的成員。|  
|**dbreadonly**|**bit**|如果資料庫已標記為唯讀，則為，值為 **1** 時，表示資料庫是唯讀的。|  
|**haspublications**|**bit**|這是指資料庫是否有任何現有的發行集; **1** 的值表示有現有的發行集。|  
|**haspullsubscriptions**|**bit**|這是指資料庫是否有任何現有的提取訂閱; **1** 值表示有現有的提取訂閱。|  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或 **1** (失敗)   
  
## <a name="remarks"></a>備註  
 **sp_helpreplicationdboption** 用於快照式、交易式和合併式複寫中。  
  
## <a name="permissions"></a>權限  
 **系統管理員（sysadmin** ）固定伺服器角色的成員可以執行任何資料庫的**sp_helpreplicationdboption** 。 **Db_owner**固定資料庫角色的成員可以執行該資料庫的**sp_helpreplicationdboption** 。  
  
## <a name="see-also"></a>另請參閱  
 [sp_replicationdboption &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
