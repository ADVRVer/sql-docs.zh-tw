---
title: sp_add_operator (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_operator
- sp_add_operator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_operator
ms.assetid: 817cd98a-4dff-4ed8-a546-f336c144d1e0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 49d7ac030eb8e391f083311fc0248b0f0752e72a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68121024"
---
# <a name="spaddoperator-transact-sql"></a>sp_add_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  建立操作員 (通知收件者) 來搭配使用警示和作業。  
  
 
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_add_operator [ @name = ] 'name'   
     [ , [ @enabled = ] enabled ]   
     [ , [ @email_address = ] 'email_address' ]   
     [ , [ @pager_address = ] 'pager_address' ]   
     [ , [ @weekday_pager_start_time = ] weekday_pager_start_time ]   
     [ , [ @weekday_pager_end_time = ] weekday_pager_end_time ]   
     [ , [ @saturday_pager_start_time = ] saturday_pager_start_time ]   
     [ , [ @saturday_pager_end_time = ] saturday_pager_end_time ]   
     [ , [ @sunday_pager_start_time = ] sunday_pager_start_time ]   
     [ , [ @sunday_pager_end_time = ] sunday_pager_end_time ]   
     [ , [ @pager_days = ] pager_days ]   
     [ , [ @netsend_address = ] 'netsend_address' ]   
     [ , [ @category_name = ] 'category' ]   
```  
  
## <a name="arguments"></a>引數  
`[ @name = ] 'name'` 操作員 （通知收件者） 的名稱。 此名稱必須是唯一的而且不能包含百分比 ( **%** ) 字元。 *名稱*已**sysname**，沒有預設值。  
  
`[ @enabled = ] enabled` 指出操作員目前狀態。 *已啟用*已**tinyint**，預設值是**1** （啟用）。 如果**0**，操作員未啟用，而且不會收到通知。  
  
`[ @email_address = ] 'email_address'` 操作員的電子郵件地址。 這個字串會直接傳遞至電子郵件系統。 *email_address*已**nvarchar(100)** ，預設值是 NULL。  
  
 您可以指定實體電子郵件地址或別名*email_address*。 例如:  
  
 '**jdoe**' **jdoe@xyz.com** '  
  
> [!NOTE]  
>  您必須針對 Database Mail 使用電子郵件地址。  
  
`[ @pager_address = ] 'pager_address'` 操作員呼叫器號碼。 這個字串會直接傳遞至電子郵件系統。 *pager_address&lt*已**narchar(100)** ，預設值是 NULL。  
  
`[ @weekday_pager_start_time = ] weekday_pager_start_time` 這段時間之後[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理程式將呼叫器通知傳給指定的操作員在工作日，從星期一到星期五。 *weekday_pager_start_time*已**int**，預設值是**090000**，這表示上午 9:00 必須用 HHMMSS 格式來輸入。  
  
`[ @weekday_pager_end_time = ] weekday_pager_end_time` 這段時間之後**SQLServerAgent**服務不再將呼叫器通知傳給指定的操作員在工作日，從星期一到星期五。 *weekday_pager_end_time*已**int**，預設值是 180000，表示下午 6:00 必須用 HHMMSS 格式來輸入。  
  
`[ @saturday_pager_start_time = ] saturday_pager_start_time` 這段時間之後**SQLServerAgent**服務會呼叫器通知傳送給指定的操作員在星期六。 *saturday_pager_start_time*已**int**，預設值是 090000，表示上午 9:00 必須用 HHMMSS 格式來輸入。  
  
`[ @saturday_pager_end_time = ] saturday_pager_end_time` 這段時間之後**SQLServerAgent**服務不再將呼叫器通知傳給指定的操作員在星期六。 *saturday_pager_end_time*是**int**，預設值是**180000**，這表示下午 6:00 必須用 HHMMSS 格式來輸入。  
  
`[ @sunday_pager_start_time = ] sunday_pager_start_time` 這段時間之後**SQLServerAgent**服務將呼叫器通知傳送給指定的操作員在星期日。 *sunday_pager_start_time*已**int**，預設值是**090000**，這表示上午 9:00 必須用 HHMMSS 格式來輸入。  
  
`[ @sunday_pager_end_time = ] sunday_pager_end_time` 這段時間之後**SQLServerAgent**服務不再將呼叫器通知傳給指定的操作員在星期日。 *sunday_pager_end_time*是**int**，預設值是**180000**，這表示下午 6:00 必須用 HHMMSS 格式來輸入。  
  
`[ @pager_days = ] pager_days` 是數字，指出操作員能夠 （遵照指定的開始/結束時間） 的天數。 *pager_days*已**tinyint**，預設值是**0**表示操作員永不便能夠收到頁面。 有效的值是從**0**透過**127**。 *pager_days*的計算方式是加入必要天數的個別值。 例如，從星期一到星期五是**2**+**4**+**8**+**16** + **32** = **62**。 下表列出一星期中各天的值。  
  
|值|描述|  
|-----------|-----------------|  
|**1**|星期日|  
|**2**|星期一|  
|**4**|星期二|  
|**8**|星期三|  
|**16**|星期四|  
|**32**|星期五|  
|**64**|星期六|  
  
`[ @netsend_address = ] 'netsend_address'` 網路訊息所要送往的操作員網路位址。 *netsend_address&lt*已**nvarchar(100)** ，預設值是 NULL。  
  
`[ @category_name = ] 'category'` 這位操作員的類別目錄的名稱。 *類別目錄*已**sysname**，預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="remarks"></a>備註  
 **sp_add_operator**必須從執行**msdb**資料庫。  
  
 電子郵件系統也支援傳呼，如果您要使用傳呼，電子郵件系統必須有「電子郵件至呼叫器」的功能。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 提供了一種簡單的圖形方式供您管理各項作業，建議您利用這個方式來建立和管理作業基礎結構。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色可以執行**sp_add_operator**。  
  
## <a name="examples"></a>範例  
 下列範例設定 `danwi` 的操作員資訊。 操作員是啟用的狀態。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會在星期一到星期五的上午 8 點至下午 5 點，利用呼叫器來傳送通知 。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_operator  
    @name = N'Dan Wilson',  
    @enabled = 1,  
    @email_address = N'danwi',  
    @pager_address = N'5551290AW@pager.Adventure-Works.com',  
    @weekday_pager_start_time = 080000,  
    @weekday_pager_end_time = 170000,  
    @pager_days = 62 ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_delete_operator &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [sp_help_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_update_operator &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
