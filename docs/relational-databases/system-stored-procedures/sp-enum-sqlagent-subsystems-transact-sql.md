---
title: "sp_enum_sqlagent_subsystems (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_enum_sqlagent_subsystems
- sp_enum_sqlagent_subsystems_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_enum_sqlagent_subsystems
ms.assetid: 019a3c9d-bac3-495b-a70a-2c19f1d2e20e
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 739da9cd2047fb3bc6171b2a5eaeced2d3cacf9f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="spenumsqlagentsubsystems-transact-sql"></a>sp_enum_sqlagent_subsystems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  列出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 子系統。  
  
||  
|-|  
|**適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。|  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_enum_sqlagent_subsystems  
```  
  
## <a name="arguments"></a>引數  
 無  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**子系統**|**nvarchar （40)**|子系統的名稱。|  
|**描述**|**nvarchar(512)**|子系統的描述。|  
|**msdb.dbo.syssubsystems**|**nvarchar(510)**|子系統所在的 DLL 模組。|  
|**agent_exe**|**nvarchar(510)**|子系統所用的可執行模組。|  
|**start_entry_point**|**nvarchar （30)**|在作業步驟執行期間，SQL Server Agent 所呼叫的程序。|  
|**event_entry_point**|**nvarchar （30)**|在作業步驟執行期間，SQL Server Agent 所呼叫的程序。|  
|**stop_entry_point**|**nvarchar （30)**|在作業步驟執行期間，SQL Server Agent 所呼叫的程序。|  
|**max_worker_threads**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 將針對這個子系統來啟動的最大執行緒數目。|  
|**syssubsystems**|**int**|子系統的識別碼。|  
  
## <a name="remarks"></a>備註  
 這個程序會列出執行個體中可用的子系統。  
  
## <a name="permissions"></a>Permissions  
 依預設，只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠執行這個預存程序。 其他使用者必須被授與 **msdb** 資料庫的 **SQLAgentOperatorRole** 固定資料庫角色。  
  
 如需詳細資訊**SQLAgentOperatorRole**，請參閱[SQL Server Agent Fixed Database Roles](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)。  
  
## <a name="see-also"></a>請參閱＜  
 [實作 SQL Server Agent 安全性](http://msdn.microsoft.com/library/d770d35c-c8de-4e00-9a85-7d03f45a0f0d)   
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)  
  
  
