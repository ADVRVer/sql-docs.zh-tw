---
description: sp_dropdistpublisher (Transact-SQL)
title: sp_dropdistpublisher (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropdistpublisher
- sp_dropdistpublisher_TSQL
helpviewer_keywords:
- sp_dropdistpublisher
ms.assetid: c0bdd3de-3be0-455c-898a-98d4660e7ce3
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2d7d0eed28b877c881cd297556755ea70bf5c674
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543509"
---
# <a name="sp_dropdistpublisher-transact-sql"></a>sp_dropdistpublisher (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  卸除散發發行者。 這個預存程序執行於任何資料庫中的散發者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_dropdistpublisher [ @publisher = ] 'publisher'  
    [ , [ @no_checks = ] no_checks ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>引數  
`[ @publisher = ] 'publisher'` 這是要卸載的發行者。 *publisher* 是 **sysname**，沒有預設值。  
  
`[ @no_checks = ] no_checks` 指定 **sp_dropdistpublisher** 是否檢查發行者是否已將伺服器卸載為散發者。 *no_checks* 是 **bit**，預設值是 **0**。  
  
 如果是 **0**，複寫會確認遠端發行者已將本機伺服器卸載為「散發者」。 如果發行者在本機，複寫會確認本機伺服器中沒有其餘發行集或散發物件。  
  
 如果是 **1**，即使無法連線到遠端發行者，還是會卸載與散發發行者相關聯的所有複寫物件。 這麼做之後，遠端發行者必須使用** \@ ignore_distributor**1 的[sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md)來卸載複寫  =  ** **。  
  
`[ @ignore_distributor = ] ignore_distributor` 指定移除發行者時，是否將散發物件保留在散發者上。 *ignore_distributor* 是 **bit** ，而且可以是下列其中一個值：  
  
 **1** = 屬於發行者的散發物件保留在散發 *者* 端。  
  
 **0** = 發行者的散發物件會在「散發 *者* 」上清除。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或 **1** (失敗)   
  
## <a name="remarks"></a>備註  
 **sp_dropdistpublisher** 用於所有類型的複寫中。  
  
 卸載「Oracle 發行者」時，如果無法卸載「發行者」 **sp_dropdistpublisher** 會傳回錯誤，而且會移除「發行者」的「散發者」物件。  
  
## <a name="example"></a>範例  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/sp-dropdistpublisher-tra_1.sql)]  
  
## <a name="permissions"></a>權限  
 只有 **系統管理員（sysadmin** ）固定伺服器角色的成員，才可以執行 **sp_dropdistpublisher**。  
  
## <a name="see-also"></a>另請參閱  
 [停用發行和散發](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sp_adddistpublisher &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [複寫預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
