---
title: sp_setsubscriptionxactseqno (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_setsubscriptionxactseqno
- sp_setsubscriptionxactseqno_TSQL
helpviewer_keywords:
- sp_setsubscriptionxactseqno
ms.assetid: cdb4e0ba-5370-4905-b03f-0b0c6f080ca6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 27a7f35a915e2bff62932124aef64984a63cbd0e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68021080"
---
# <a name="spsetsubscriptionxactseqno-transact-sql"></a>sp_setsubscriptionxactseqno (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在疑難排解期間使用，以指定使用的記錄序號 (LSN)，讓散發代理程式，以開始下一個交易在上一個傳送的交易。 一旦重新啟動，散發代理程式會傳回交易大於此浮水印 (LSN) 從散發資料庫快取 (msrepl_commands)。 這個預存程序執行於訂閱資料庫的訂閱者端。 不支援非 SQL Server 訂閱者使用這個項目。  
  
> [!CAUTION]  
>  不正確使用這個預存程序或指定了不正確的 LSN 值，散發代理程式可能會還原訂閱者端先前所套用的變更，也可能會略過所有其餘變更。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_setsubscriptionxactseqno [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @xact_seqno = ] xact_seqno   
```  
  
## <a name="arguments"></a>引數  
`[ @publisher = ] 'publisher'` 是 「 發行者 」 的名稱。 *發行者*已**sysname**，沒有預設值。  
  
`[ @publisher_db = ] 'publisher_db'` 是發行集資料庫的名稱。 *publisher_db*已**sysname**，沒有預設值。 針對非 SQL Server 發行者， *publisher_db*是散發資料庫的名稱。  
  
`[ @publication = ] 'publication'` 是發行集名稱。 *發行集*已**sysname**，沒有預設值。 當一個以上的發行集共用散發代理程式時，您必須指定 ALL 值*發行集*。  
  
`[ @xact_seqno = ] xact_seqno` 是套用在訂閱者端的散發者端之下一項交易的 LSN。 *xact_seqno*已**varbinary(16)** ，沒有預設值。  
  
## <a name="result-set"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**ORIGINAL XACT_SEQNO**|**varbinary(16)**|訂閱者端所要套用之下一項交易的原始 LSN。|  
|**UPDATED XACT_SEQNO**|**varbinary(16)**|訂閱者端所要套用之下一項交易的更新 LSN。|  
|**訂用帳戶資料流計數**|**int**|在上一次同步處理期間所用的訂閱資料流數目。|  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_setsubscriptionxactseqno**用於異動複寫中。  
  
 **sp_setsubscriptionxactseqno**無法用於對等項目-異動複寫拓撲中。  
  
 **sp_setsubscriptionxactseqno**可以用來略過特定的交易，會導致錯誤發生時套用在訂閱者。 失敗時及之後停止散發代理程式，請呼叫[sp_helpsubscriptionerrors &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helpsubscriptionerrors-transact-sql.md)散發者端擷取失敗的交易的 xact_seqno 值，然後呼叫**sp_setsubscriptionxactseqno**，將此值傳遞*xact_seqno*。 這可以確保只會處理在這個 LSN 之後的命令。  
  
 指定的值為**0** for *xact_seqno*散發資料庫中的所有暫止命令傳遞給訂閱者。  
  
 **sp_setsubscriptionxactseqno**如果 「 散發代理程式會使用多個訂閱資料流可能會失敗。  
  
 當發生這個錯誤時，您必須利用單一訂閱資料流來執行散發代理程式。 如需詳細資訊，請參閱 [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色或**db_owner**固定的資料庫角色可以執行**sp_setsubscriptionxactseqno**。  
  
## <a name="see-more"></a>查看更多

[部落格：如何略過的交易](https://repltalk.com/2019/05/28/how-to-skip-a-transaction/)  
