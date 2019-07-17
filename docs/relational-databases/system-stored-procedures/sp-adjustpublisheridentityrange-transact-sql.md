---
title: sp_adjustpublisheridentityrange & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adjustpublisheridentityrange_TSQL
- sp_adjustpublisheridentityrange
helpviewer_keywords:
- sp_adjustpublisheridentityrange
ms.assetid: 64f111fd-fb7d-4459-93f7-65f0f8dd7efe
author: stevestein
ms.author: sstein
ms.openlocfilehash: eb9fdd324ba6275cd20f99a32f0a82aa112626b1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68117883"
---
# <a name="spadjustpublisheridentityrange-transact-sql"></a>sp_adjustpublisheridentityrange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  調整發行集的識別範圍，再依據發行集的臨界值來重新配置新的範圍。 這個預存程序執行於發行集資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_adjustpublisheridentityrange [ [ @publication = ] 'publication' ]  
    [ , [ @table_name = ] 'table_name' ]  
    [ , [ @table_owner= ] 'table_owner' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @publication = ] 'publication'` 是重新配置新識別範圍的發行集的名稱。 *發行集*已**sysname**，預設值是 NULL。  
  
`[ @table_name = ] 'table_name'` 是重新配置新識別範圍的資料表名稱。 *table_name*已**sysname**，預設值是 NULL。  
  
`[ @table_owner = ] 'table_owner'` 是在發行者端資料表的擁有者。 *table_owner*已**sysname**，預設值是 NULL。 如果*table_owner*未指定，會使用目前使用者的名稱。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_adjustpublisheridentityrange**用於所有類型的複寫。  
  
 如果是啟用了自動識別範圍的發行集，散發代理程式或合併代理程式便能夠針對基於臨界值的發行集識別範圍的自動調整來進行回應。 不過，如果基於某些原因的散發代理程式 」 或 「 合併代理程式尚未執行的一段時間，並識別範圍資源已嚴重耗用到臨界值的點，使用者可以呼叫**sp_adjustpublisheridentityrange**若要配置發行者新的值範圍。  
  
 執行時**sp_adjustpublisheridentityrange**，可以是*發行集*或是*table_name*必須指定。 如果同時指定這兩者，或兩者都未指定，就會傳回錯誤。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色或**db_owner**固定的資料庫角色可以執行**sp_adjustpublisheridentityrange**。  
  
## <a name="see-also"></a>另請參閱  
 [複寫識別資料行](../../relational-databases/replication/publish/replicate-identity-columns.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
