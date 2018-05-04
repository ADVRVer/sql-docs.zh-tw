---
title: sp_dropanonymousagent (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- sp_dropanonymousagent
- sp_dropanonymousagent_TSQL
helpviewer_keywords:
- sp_dropanonymousagent
ms.assetid: 4cb96efa-9358-44a3-a8ee-a7e181bed089
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f9e7a1f68199367f2f40716b2295452eb2725a53
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="spdropanonymousagent-transact-sql"></a>sp_dropanonymousagent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  從發行者卸除在散發者端之複寫監視的匿名代理程式。 這個預存程序執行於任何資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_dropanonymousagent [ @subid= ] sub_id    , [ @type= ] type  
```  
  
## <a name="arguments"></a>引數  
 [  **@subid=**] *sub_id*  
 這是匿名訂閱的全域識別碼。 *sub_id*是**uniqueidentifier**，沒有預設值。 此識別碼可以擷取訂閱者端使用**sp_helppullsubscription**。 中的值**subid**傳回的結果集欄位是這個全域識別碼。  
  
 [  **@type=**]*類型*  
 這是訂閱的類型。 *型別*是**int**，沒有預設值。 有效值為**1**或**2**。 指定**1**，如果快照式複寫或異動複寫使用 「 散發代理程式。 指定**2**，如果合併式複寫使用 「 合併代理程式。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_dropanonymousagent**用於所有複寫類型。  
  
 這個預存程序只能用來卸除匿名訂閱代理程式，無法用來卸除已知的訂閱。  
  
## <a name="permissions"></a>Permissions  
 只有成員**db_owner**散發資料庫中的固定的資料庫角色可以執行**sp_dropanonymousagent**。  
  
## <a name="see-also"></a>另請參閱  
 [複寫預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
