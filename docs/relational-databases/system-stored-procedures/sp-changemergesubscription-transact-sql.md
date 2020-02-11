---
title: sp_changemergesubscription （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changemergesubscription_TSQL
- sp_changemergesubscription
helpviewer_keywords:
- sp_changemergesubscription
ms.assetid: fd820f35-c189-4e2d-884d-b60c1c469f58
author: stevestein
ms.author: sstein
ms.openlocfilehash: c205bab104bd81eda3e7d14dc30844352caa7f66
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124874"
---
# <a name="sp_changemergesubscription-transact-sql"></a>sp_changemergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  變更合併發送訂閱的所選屬性。 這個預存程序執行於發行集資料庫的發行者端。  
  
> [!IMPORTANT]  
>  當利用遠端散發者來設定發行者時，提供給所有參數的值 (包括 *job_login* 和 *job_password*) 都會以純文字的方式傳給散發者。 您應該先加密「發行者」及其遠端「散發者」之間的連接，再執行這個預存程序。 如需詳細資訊，請參閱[啟用 Database Engine 的加密連接 &#40;SQL Server 組態管理員&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)。  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_changemergesubscription [ [ @publication= ] 'publication' ]  
    [ , [ @subscriber= ] 'subscriber'  
    [ , [ @subscriber_db= ] 'subscriber_db' ]  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @publication = ] 'publication'`這是要變更的發行集名稱。 *發行*集是**sysname**，預設值是 Null。 發行集必須已存在，且必須符合識別碼的規則。  
  
`[ @subscriber = ] 'subscriber'`這是訂閱者的名稱。 *訂閱者*是**sysname**，預設值是 Null。  
  
`[ @subscriber_db = ] 'subscriber_db'`這是訂閱資料庫的名稱。 *subscriber_db*是**sysname**，預設值是 Null。  
  
`[ @property = ] 'property'`這是給定發行集要變更的屬性。 *屬性*是**sysname**，它可以是資料表中的其中一個值。  
  
`[ @value = ] 'value'`這是指定之*屬性*的新值。 *value*是**Nvarchar （255）**，它可以是資料表中的其中一個值。  
  
|屬性|值|描述|  
|--------------|-----------|-----------------|  
|**描述**||這個合併訂閱的描述。|  
|**優先順序**||這是訂閱優先權。 在偵測到衝突時，預設解析程式會利用優先權挑選贏的一方。|  
|**merge_job_login**||用來執行代理程式之 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帳戶的登入。|  
|**merge_job_password**||用來執行代理程式之 Windows 帳戶的密碼。|  
|**publisher_security_mode**|**1**|當連接到發行者時，使用 Windows 驗證。|  
||**0**|當連接到發行者時，使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證。|  
|**publisher_login**||發行者的登入名稱。|  
|**publisher_password**||提供之發行者登入的增強式密碼。|  
|**subscriber_security_mode**|**1**|當連接到發行者時，使用 Windows 驗證。|  
||**0**|當連接到訂閱者時，使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證。|  
|**subscriber_login**||訂閱者的登入名稱。|  
|**subscriber_password**||提供之訂閱者登入的增強式密碼。|  
|**sync_type**|**自動**|先將發行資料表的結構描述和初始資料傳送給訂閱者。|  
||**無**|訂閱者已有發行資料表的結構描述和初始資料；一律會傳送系統資料表和資料。|  
|**use_interactive_resolver**|**真正**|可讓您以互動方式來解決接受互動式解決之所有發行項的衝突。|  
||**false**|衝突是利用預設解析程式或自訂解析程式加以自動解析。|  
|NULL (預設值)|NULL (預設值)||  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功）或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_changemergesubscription**用於合併式複寫中。  
  
 變更代理程式的登入或密碼之後，您必須先停止並重新啟動代理程式，變更才會生效。  
  
## <a name="permissions"></a>權限  
 只有**系統管理員（sysadmin** ）固定伺服器角色或**db_owner**固定資料庫角色的成員，才能夠執行**sp_changemergesubscription**。  
  
## <a name="see-also"></a>另請參閱  
 [sp_addmergesubscription &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
