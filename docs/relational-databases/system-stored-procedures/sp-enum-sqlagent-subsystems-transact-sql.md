---
title: sp_enum_sqlagent_subsystems (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_enum_sqlagent_subsystems
- sp_enum_sqlagent_subsystems_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_sqlagent_subsystems
ms.assetid: 019a3c9d-bac3-495b-a70a-2c19f1d2e20e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5aac3e1471f969ea324008c03f97b9b26c05c4ec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47790206"
---
# <a name="spenumsqlagentsubsystems-transact-sql"></a>sp_enum_sqlagent_subsystems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  列出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 子系統。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_enum_sqlagent_subsystems  
```  
  
## <a name="arguments"></a>引數  
 None  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**subsystem**|**nvarchar(40)**|子系統的名稱。|  
|**description**|**nvarchar(512)**|子系統的描述。|  
|**subsystem_dll**|**nvarchar(510)**|子系統所在的 DLL 模組。|  
|**agent_exe**|**nvarchar(510)**|子系統所用的可執行模組。|  
|**start_entry_point**|**nvarchar(30)**|在作業步驟執行期間，SQL Server Agent 所呼叫的程序。|  
|**event_entry_point**|**nvarchar(30)**|在作業步驟執行期間，SQL Server Agent 所呼叫的程序。|  
|**stop_entry_point**|**nvarchar(30)**|在作業步驟執行期間，SQL Server Agent 所呼叫的程序。|  
|**max_worker_threads**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 將針對這個子系統來啟動的最大執行緒數目。|  
|**subsystem_id**|**int**|子系統的識別碼。|  
  
## <a name="remarks"></a>備註  
 這個程序會列出執行個體中可用的子系統。  
  
## <a name="permissions"></a>Permissions  
 依預設，只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠執行這個預存程序。 其他使用者必須被授與 **msdb** 資料庫的 **SQLAgentOperatorRole** 固定資料庫角色。  
  
 如需詳細資訊**SQLAgentOperatorRole**，請參閱[SQL Server Agent 固定資料庫角色](../../ssms/agent/sql-server-agent-fixed-database-roles.md)。  
  
## <a name="see-also"></a>另請參閱  
 [實作 SQL Server Agent 安全性](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)  
  
  
