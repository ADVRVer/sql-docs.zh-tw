---
title: dbo.sysproxylogin （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysproxylogin_TSQL
- sysproxylogin_TSQL
- dbo.sysproxylogin
- sysproxylogin
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxylogin system table
ms.assetid: 433d33cb-bdf2-47bb-af78-2a40b7c8dfce
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 67e119b52b2dcb741ce1c63b343970e3152ccee5
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890414"
---
# <a name="dbosysproxylogin-transact-sql"></a>dbo.sysproxylogin (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  記錄與每個 SQL Server Agent Proxy 帳戶相關的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。 此資料表會儲存在**msdb**資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Proxy 帳戶的識別碼。 這個值會對應至**sysproxies**資料表中的**proxy_id**資料行。|  
|**sid**|**Varbinary （85）**|適用于 SQL Server 登入的 Microsoft Windows *security_identifier* 。|  
|**principal_id**|**int**|有權使用指定子系統步驟的 Proxy 帳戶之使用者或群組的識別碼。|  
|**flags**|**int**|登入類型：<br /><br /> **0** = Windows 使用者或群組，以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定系統角色<br /><br /> **2**  = **msdb**資料庫角色|  
  
## <a name="remarks"></a>備註  
 只有**系統管理員（sysadmin** ）固定伺服器角色的成員，才能夠存取此資料表。  
  
## <a name="see-also"></a>另請參閱  
 [dbo.sysproxy &#40;Transact-sql&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
