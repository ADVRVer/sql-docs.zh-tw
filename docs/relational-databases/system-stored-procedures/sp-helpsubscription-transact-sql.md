---
title: sp_helpsubscription (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
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
f1_keywords:
- sp_helpsubscription_TSQL
- sp_helpsubscription
helpviewer_keywords:
- sp_helpsubscription
ms.assetid: ff96bcbf-e2b9-4da8-8515-d80d4ce86c16
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 695442f30d62a651521dc5b90027a4d43daa7dde
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpsubscription-transact-sql"></a>sp_helpsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  列出特定發行集、發行項、訂閱者或訂閱組的相關聯訂閱資訊。 這個預存程序執行於發行集資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helpsubscription [ [ @publication = ] 'publication' ]   
    [ , [ @article = ] 'article' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @destination_db = ] 'destination_db' ]   
    [ , [ @found=] found OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引數  
 [ **@publication =** ] **'***publication***'**  
 這是關聯的發行集名稱。 *發行集*是**sysname**，預設值是**%**，它會傳回此伺服器的所有訂用帳戶資訊。  
  
 [  **@article=** ] **'***文章***'**  
 這是發行項的名稱。 *發行項*是**sysname**，預設值是**%**，它會傳回與選定發行集和訂閱者的所有訂用帳戶資訊。 如果**所有**，只有一個項目會傳回完整的訂用帳戶的發行集上。  
  
 [  **@subscriber=** ] **'***訂閱者***'**  
 這是取得訂閱資訊的相關訂閱者名稱。 *訂閱者*是**sysname**，預設值是**%**，它會傳回與所選取的發行集和發行項的所有訂用帳戶資訊。  
  
 [  **@destination_db=** ] **'***destination_db***'**  
 這是目的地資料庫的名稱。 *destination_db*是**sysname**，預設值是**%**。  
  
 [  **@found=** ] **'***找到***'**輸出  
 這是表示傳回資料列的旗標。 *找到*是**int**和一個 OUTPUT 參數，預設值是 23456。  
  
 **1**表示找到發行集。  
  
 **0**指出找不到發行集。  
  
 [ **@publisher**=] **'***發行者***'**  
 這是發行者的名稱。 *發行者*是**sysname**，而且預設為目前伺服器的名稱。  
  
> [!NOTE]  
>  *發行者*不應指定，除非它是 「 Oracle 發行者 」。  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**訂閱者**|**sysname**|訂閱者的名稱。|  
|**發行集**|**sysname**|發行集的名稱。|  
|**article**|**sysname**|發行項的名稱。|  
|**目的地資料庫**|**sysname**|複寫的資料放在其中的目的地資料庫名稱。|  
|**訂閱狀態**|**tinyint**|訂閱狀態：<br /><br /> **0** = 非使用中<br /><br /> **1** = 訂閱<br /><br /> **2** = 作用中|  
|**同步處理類型**|**tinyint**|訂閱同步處理類型：<br /><br /> **1** = 自動<br /><br /> **2** = 無|  
|**訂用帳戶類型**|**int**|訂閱的類型：<br /><br /> **0** = 發送<br /><br /> **1** = 提取<br /><br /> **2** = 匿名|  
|**完整訂閱**|**bit**|訂閱是否針對發行集中的所有發行項：<br /><br /> **0** = 否<br /><br /> **1** = 是|  
|**訂用帳戶名稱**|**nvarchar(255)**|訂閱的名稱。|  
|**更新模式**|**int**|**0** = 唯讀<br /><br /> **1** = 立即更新訂閱|  
|**散發作業識別碼**|**binary(16)**|散發代理程式的作業識別碼。|  
|**loopback_detection**|**bit**|回送偵測會判斷散發代理程式是否將起源於訂閱者端的交易傳回給訂閱者：<br /><br /> **0** = 傳回。<br /><br /> **1** = 不傳回。<br /><br /> 搭配雙向異動複寫來使用。 如需詳細資訊，請參閱[雙向異動複寫](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md)。|  
|**offload_enabled**|**bit**|指定是否已將複寫代理程式的卸載執行設成執行於訂閱者端。<br /><br /> 如果**0**，在發行者端執行代理程式。<br /><br /> 如果**1**，訂閱者端執行代理程式。|  
|**offload_server**|**sysname**|啟用遠端代理程式啟動的伺服器名稱。 如果是 NULL，然後列出的目前 offload_server 中[MSdistribution_agents](../../relational-databases/system-tables/msdistribution-agents-transact-sql.md)使用資料表。|  
|**dts_package_name**|**sysname**|指定 Data Transformation Services (DTS) 封裝的名稱。|  
|**dts_package_location**|**int**|如果訂閱指派了 DTS 封裝，便是這項封裝的位置。 如果封裝時，值為**0**指定封裝的位置在**散發者**。 值為**1**指定**訂閱者**。|  
|**subscriber_security_mode**|**smallint**|安全性模式，在訂閱者，其中**1**表示 Windows 驗證和**0**表示[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]驗證。|  
|**subscriber_login**|**sysname**|這是在訂閱者端的登入名稱。|  
|**subscriber_password**||永遠不傳回實際的訂閱者密碼。 結果為已遮罩，由 「**\*\*\*\*\*\***"字串。|  
|**job_login**|**sysname**|用來執行散發代理程式之 Windows 帳戶的名稱。|  
|**job_password**||永遠不傳回實際的作業密碼。 結果為已遮罩，由 「**\*\*\*\*\*\***"字串。|  
|**distrib_agent_name**|**nvarchar(100)**|同步處理訂閱的代理程式作業的名稱。|  
|**subscriber_type**|**tinyint**|這是訂閱者的類型，它可以是下列其中之一：<br /><br /> **0** = SQL Server 訂閱者<br /><br /> **1** = ODBC 資料來源伺服器<br /><br /> **2** = Microsoft JET 資料庫 （已被取代）<br /><br /> **3** = OLE DB 提供者|  
|**subscriber_provider**|**sysname**|用來登錄非 SQL Server 資料來源之 OLE DB 提供者的唯一程式化識別碼 (PROGID)。|  
|**subscriber_datasource**|**nvarchar(4000)**|OLE DB 提供者所了解的資料來源名稱。|  
|**subscriber_providerstring**|**nvarchar(4000)**|OLE DB 提供者特定的連接字串，用來識別資料來源。|  
|**subscriber_location**|**nvarchar(4000)**|OLE DB 提供者所了解的資料庫位置|  
|**subscriber_catalog**|**sysname**|建立 OLE DB 提供者連接時所用的目錄。|  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_helpsubscription**用於快照式和異動複寫。  
  
## <a name="permissions"></a>Permissions  
 執行權限預設為**公用**角色。 使用者是使用者所建立之訂閱的唯一傳回資訊。 所有訂閱的資訊傳回給**sysadmin** 「 發行者 」 或成員的固定的伺服器角色**db_owner**發行集資料庫上的固定的資料庫角色。  
  
## <a name="see-also"></a>另請參閱  
 [sp_addsubscription &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubstatus &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_dropsubscription &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
