---
title: sysdbmaintplans （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplans_TSQL
- sysdbmaintplans
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplans system table
ms.assetid: 0363296a-3082-48a9-9eb5-a1020b2f541a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b787b62f1f4f68c279449aa9bf4bc905898ec66d
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82803062"
---
# <a name="sysdbmaintplans-transact-sql"></a>sysdbmaintplans (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  這個資料表會包含在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，以保存從舊版 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升級而來之執行個體的現有資訊。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不會變更此資料表的內容。 此資料表會儲存在**msdb**資料庫中。  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  

  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|資料庫維護計畫識別碼。|  
|**plan_name**|**sysname**|資料庫維護計畫名稱。|  
|**date_created**|**datetime**|資料庫維護計畫的建立日期。|  
|**主人**|**sysname**|資料庫維護計畫的擁有者。|  
|**max_history_rows**|**int**|用來將資料庫維護計畫的記錄記載到系統資料表中，所配置的最大資料列數。|  
|**remote_history_server**|**sysname**|可寫入記錄報表之遠端伺服器的名稱。|  
|**max_remote_history_rows**|**int**|在遠端伺服器系統資料表中，可寫入記錄報表的資料列最大配置列數。|  
|**user_defined_1**|**int**|預設值是 NULL。|  
|**user_defined_2**|**Nvarchar （100）**|預設值是 NULL。|  
|**user_defined_3**|**datetime**|預設值是 NULL。|  
|**user_defined_4**|**uniqueidentifier**|預設值是 NULL。|  
|**log_shipping**|**bit**|記錄傳送狀態：<br /><br /> **0** = 已停用**1** = 已啟用|  
  
  
