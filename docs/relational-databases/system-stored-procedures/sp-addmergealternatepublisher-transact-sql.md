---
title: sp_addmergealternatepublisher (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergealternatepublisher_TSQL
- sp_addmergealternatepublisher
helpviewer_keywords:
- sp_addmergealternatepublisher
ms.assetid: de46e0b1-d946-4021-bff6-2d8e3187656d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7927eef8105fff23a3fe790f32794fe5dd44cdae
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769186"
---
# <a name="spaddmergealternatepublisher-transact-sql"></a>sp_addmergealternatepublisher (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  新增訂閱者使用替代同步處理夥伴的能力。 發行集屬性必須指定訂閱者能夠與其他發行者同步處理。 這個預存程序執行於訂閱資料庫的訂閱者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_addmergealternatepublisher [ @publisher= ] 'publisher'  
          , [ @publisher_db= ] 'publisher_db'  
          , [ @publication= ] 'publication'  
          , [ @alternate_publisher= ] 'alternate_synchronization_partner'  
          , [ @alternate_publisher_db= ] 'alternate_publisher_db'  
          , [ @alternate_publication= ] 'alternate_synchronization_partner'  
     , [ @alternate_distributor= ] 'alternate_distributor'   
    [ , [ @friendly_name= ] 'friendly_name' ]   
    [ , [ @reserved= ] 'reserved' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @publisher = ] 'publisher'`這是發行者的名稱。 *publisher*是**sysname**, 沒有預設值。  
  
`[ @publisher_db = ] 'publisher_db'`這是發行集資料庫的名稱。 *publisher_db*是**sysname**, 沒有預設值。  
  
`[ @publication = ] 'publication'`這是發行集的名稱。 *發行*集是**sysname**, 沒有預設值。  
  
`[ @alternate_publisher = ] 'alternate_synchronization_partner'`這是替代發行者的名稱。 *alternate_synchronization_partner*是**sysname**, 沒有預設值。  
  
`[ @alternate_publisher_db = ] 'alternate_publisher_db'`這是替代發行者上的發行集資料庫名稱。 *alternate_publisher_db*是**sysname**, 沒有預設值。  
  
`[ @alternate_publication = ] 'alternate_synchronization_partner'`這是替代同步處理夥伴上的發行集名稱。 *alternate_synchronization_partner*是**sysname**, 沒有預設值。  
  
`[ @alternate_distributor = ] 'alternate_distributor'`這是替代同步夥伴的散發者名稱。 *alternate_distributor*是**sysname**, 沒有預設值。  
  
`[ @friendly_name = ] 'friendly_name'`這是可以識別組成替代同步處理夥伴之「發行者」、「發行集」和「散發者」關聯的「顯示名稱」。 *friendly_name*是**Nvarchar (255)** , 預設值是 Null。  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或**1** (失敗)  
  
## <a name="remarks"></a>備註  
 **sp_addmergealternatepublisher**用於合併式複寫中。  
  
## <a name="permissions"></a>Permissions  
 只有**系統管理員 (sysadmin** ) 固定伺服器角色或**db_owner**固定資料庫角色的成員, 才能夠執行**sp_addmergealternatepublisher**。  
  
## <a name="see-also"></a>另請參閱  
 [sp_dropmergealternatepublisher &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropmergealternatepublisher-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
