---
title: dbo.sysproxylogin (Transact-SQL) | Microsoft Docs
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 00a3b3b53bcede7f43aad556465358b957331f45
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62470680"
---
# <a name="dbosysproxylogin-transact-sql"></a>dbo.sysproxylogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  記錄與每個 SQL Server Agent Proxy 帳戶相關的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。 這份資料表儲存在**msdb**資料庫。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Proxy 帳戶的識別碼。 這個值會對應到**proxy_id**中的資料行**sysproxies**資料表。|  
|**sid**|**varbinary(85)**|Microsoft Windows *security_identifier&lt* SQL Server 登入。|  
|**principal_id**|**int**|有權使用指定子系統步驟的 Proxy 帳戶之使用者或群組的識別碼。|  
|**flags**|**int**|登入類型：<br /><br /> **0** = Windows 使用者或群組，和[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]登入。<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定的系統角色<br /><br /> **2** = **msdb**資料庫角色|  
  
## <a name="remarks"></a>備註  
 只有成員**sysadmin**固定的伺服器角色可以存取這份資料表。  
  
## <a name="see-also"></a>另請參閱  
 [dbo.sysproxies &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
