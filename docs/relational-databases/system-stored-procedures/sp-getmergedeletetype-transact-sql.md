---
title: sp_getmergedeletetype （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_getmergedeletetype
- sp_getmergedeletetype_TSQL
helpviewer_keywords:
- sp_getmergedeletetype
ms.assetid: 64450e4d-844d-4176-874e-f3845536f7d2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 00a7499fb3050a5ab13fa3e9b454b4335200f55a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731659"
---
# <a name="sp_getmergedeletetype-transact-sql"></a>sp_getmergedeletetype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  傳回合併刪除的類型。 這個預存程序執行於發行集資料庫的發行者端，或訂閱資料庫的訂閱者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_getmergedeletetype [ @source_object = ] 'source_object', [ @rowguid =] 'rowguid', [ @delete_type=] delete_type OUTPUT  
```  
  
## <a name="arguments"></a>引數  
`[ @source_object = ] 'source_object'`這是來源物件的名稱。 *source_object*是**Nvarchar （386）**，沒有預設值。  
  
`[ @rowguid = ] 'rowguid'`這是刪除類型的資料列識別碼。 *rowguid*是**uniqueidentifier**，沒有預設值。  
  
`[ @delete_type = ] delete_type OUTPUT`這是表示刪除類型的程式碼。 *delete_type*是**int**，沒有預設值。 *delete_type*也是輸出參數，而且可以是下列其中一個值。  
  
|值|描述|  
|-----------|-----------------|  
|**1**|使用者刪除|  
|**5**|部分刪除|  
|**6**|系統刪除|  
  
## <a name="remarks"></a>備註  
 **sp_getmergedeletetype**用於合併式複寫中。  
  
## <a name="permissions"></a>權限  
 只有**系統管理員（sysadmin** ）固定伺服器角色或**db_owner**固定資料庫角色的成員，才能夠執行**sp_getmergedeletetype**。  
  
## <a name="see-also"></a>另請參閱  
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
