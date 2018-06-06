---
title: sp_markpendingschemachange (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/04/2017
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
- sp_markpendingschemachange
- sp_markpendingschemachange_TSQL
helpviewer_keywords:
- sp_markpendingschemachange
ms.assetid: 01100309-7bef-4154-85bf-f18489577e37
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: e3bfd0bb51e6d269b84fdb57a5a64139ce23cedc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="spmarkpendingschemachange-transact-sql"></a>sp_markpendingschemachange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  用來支援合併式發行集，使管理員能夠略過所選的暫止結構描述變更，因而不會複寫它們。 這個預存程序執行於發行集資料庫的發行者端。  
  
> [!CAUTION]  
>  這個預存程序可以防止複寫結構描述變更。 只有在試過其他方法 (如重新初始化)，且效能成本太高時，才應該利用這個預存程序來解決問題。  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_markpendingschemachange [@publication = ] 'publication'  
    [ , [ @schemaversion = ] schemaversion ]  
    [ , [ @status = ] 'status' ]  
```  
  
## <a name="arguments"></a>引數  
 [**@publication=** ] **'***發行集***'**  
 這是發行集的名稱。 *發行集*是**sysname**，沒有預設值。  
  
 [  **@schemaversion=** ] *schemaversion*  
 識別暫止結構描述變更。 *schemaversion*是**int**，預設值是**0**。 使用[sp_enumeratependingschemachanges &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-enumeratependingschemachanges-transact-sql.md)列出發行集的暫止結構描述變更。  
  
 [  **@status=** ] **'***狀態***'**  
 這是指是否將略過暫止結構描述變更。 *狀態*是**nvarchar （10)** 預設值是**active**。 如果值*狀態*是**略過**，然後選取結構描述變更不會複寫。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_markpendingschemachange**用於合併式複寫。  
  
 **sp_markpendingschemachange**是預存程序適用於合併式複寫可支援性和其他修正動作，重新初始化，例如無法更正這種情況，或在成本太高時，才應該使用效能的條款。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色或**db_owner**固定的資料庫角色可以執行**sp_markpendingschemachange**。  
  
## <a name="see-also"></a>另請參閱  
 [sysmergeschemachange &#40;Transact SQL&#41;](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  
