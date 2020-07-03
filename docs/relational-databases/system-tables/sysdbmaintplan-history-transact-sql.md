---
title: sysdbmaintplan_history （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_history_TSQL
- sysdbmaintplan_history
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_history system table
ms.assetid: 02d36f08-ac93-4463-bb59-284c5cd6ed04
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ec49500e94a22e8ab91513fa9436cd6d21bf7959
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85881420"
---
# <a name="sysdbmaintplan_history-transact-sql"></a>sysdbmaintplan_history (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  此資料表會儲存在**msdb**資料庫中。  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**sequence_id**|**int**|資料庫維護計畫執行記錄的順序。|  
|**plan_id**|**uniqueidentifier**|資料庫維護計畫識別碼。|  
|**plan_name**|**sysname**|資料庫維護計畫名稱。|  
|**database_name**|**sysname**|資料庫維護計畫之相關資料庫的名稱。|  
|**server_name**|**sysname**|系統名稱。|  
|**activity**|**nvarchar(128)**|資料庫維護計畫所執行的活動 (如備份交易記錄等)。|  
|**成功**|**bit**|**0** = 成功**1** = 失敗|  
|**end_time**|**datetime**|動作完成的時間。|  
|**duration**|**int**|完成資料庫維護計畫動作所需要的時間長度。|  
|**start_time**|**datetime**|動作開始的時間。|  
|**error_number**|**int**|失敗時所報告的錯誤號碼。|  
|**message**|**nvarchar(512)**|**Sqlmaint**所產生的訊息。|  
  
  
