---
title: sp_MSchange_logreader_agent_properties (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_MSchange_logreader_agent_properties_TSQL
- sp_MSchange_logreader_agent_properties
helpviewer_keywords:
- sp_MSchange_logreader_agent_properties
ms.assetid: 925df9d3-a041-4046-8e17-c47f40edb86d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3db4c300cad5f38b46b73b2edc065a5b98ec90f0
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54130808"
---
# <a name="spmschangelogreaderagentproperties-transact-sql"></a>sp_MSchange_logreader_agent_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  變更會在執行記錄讀取器代理程式作業的屬性[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]或更新版本散發者。 當發行者執行於 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 的執行個體時，系統會利用這個預存程序來變更屬性。 這個預存程序執行於散發資料庫的散發者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_MSchange_logreader_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publisher_security_mode = ] publisher_security_mode  
        , [ @publisher_login = ] 'publisher_login'  
        , [ @publisher_password = ] 'publisher_password'   
        , [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
        , [ @publisher_type = ] 'publisher_type'  
```  
  
## <a name="arguments"></a>引數  
 [ **@publisher** =] **'**_發行者_**'**  
 這是發行者的名稱。 *發行者*已**sysname**，沒有預設值。  
  
 [  **@publisher_db=** ] **'**_publisher_db_**'**  
 這是發行集資料庫的名稱。 *publisher_db*已**sysname**，沒有預設值。  
  
 [ **@publisher_security_mode**=] *publisher_security_mode*  
 這是當連接到發行者時使用的安全性模式。 *publisher_security_mode*已**smallint**，沒有預設值。  
  
 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]驗證。  
  
 **1**指定 Windows 驗證。  
  
 [ **@publisher_login**=] **'**_publisher_login_**'**  
 這是連接到發行者時所用的登入。 *publisher_login*已**sysname**，沒有預設值。 *publisher_login*時，必須指定*publisher_security_mode*是**0**。 如果*publisher_login*為 NULL 並*publisher_security_mode*是**1**，在指定的 Windows 帳戶*job_login*將使用當連接到發行者。  
  
 [ **@publisher_password**=] **'**_publisher_password_**'**  
 這是連接到發行者時所用的密碼。 *publisher_password*已**sysname**，沒有預設值。  
  
 [ **@job_login**=] **'**_job_login_**'**  
 這是用來執行代理程式之 Windows 帳戶的登入。 *job_login*已**nvarchar(257)**，沒有預設值。 *無法變更為非*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *發行者。*  
  
 [ **@job_password**=] **'**_job_password_**'**  
 這是用來執行代理程式之 Windows 帳戶的密碼。 *job_password*已**sysname**，沒有預設值。  
  
 [ **@publisher_type**=] **'**_publisher_type_**'**  
 指定當發行者不是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中執行時的發行者類型。 *publisher_type*已**sysname**，而且可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**MSSQLSERVER**|指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 發行者。|  
|**ORACLE**|指定標準 Oracle 發行者。|  
|**ORACLE GATEWAY**|指定 Oracle Gateway 發行者。|  
  
 如需有關 Oracle 發行者 」 與 「 Oracle Gateway 發行者之間的差異的詳細資訊，請參閱 < [Oracle 發行概觀](../../relational-databases/replication/non-sql/oracle-publishing-overview.md)。  
  
## <a name="remarks"></a>備註  
 **sp_MSchange_logreader_agent_properties**用於異動複寫中。  
  
 執行時，您必須指定所有參數**sp_MSchange_logreader_agent_properties**。 執行[sp_helplogreader_agent &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md)若要傳回之記錄讀取器代理程式作業目前的屬性。  
  
 變更代理程式的登入或密碼之後，您必須先停止並重新啟動代理程式，變更才會生效。  
  
 當 「 發行者 」 端執行的執行個體上[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]或更新版本，您應該使用[sp_changelogreader_agent](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md)來變更記錄讀取器代理程式的屬性。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**散發者端的固定的伺服器角色可以執行**sp_MSchange_logreader_agent_properties**。  
  
## <a name="see-also"></a>另請參閱  
 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)  
  
  
