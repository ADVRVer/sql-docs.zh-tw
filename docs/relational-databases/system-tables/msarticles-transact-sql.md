---
title: MSarticles （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSarticles
- MSarticles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSarticles system table
ms.assetid: 1acd79a5-b3e2-4161-9592-7acc2a41ba38
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: daec387a9be288a44cbecc286bd77784ad776374
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85753957"
---
# <a name="msarticles-transact-sql"></a>MSarticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  **MSarticles**資料表會針對發行者所複寫的每個發行項，各包含一個資料列。 這份資料表儲存在散發資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|發行者的識別碼。|  
|**publisher_db**|**sysname**|發行者資料庫的名稱。|  
|**publication_id**|**int**|發行集的識別碼。|  
|**文章**|**sysname**|發行項的名稱。|  
|**article_id**|**int**|發行項的識別碼。|  
|**destination_object**|**sysname**|在訂閱者端建立之資料表的名稱。|  
|**source_owner**|**sysname**|在發行者端的來源資料表之結構描述名稱。|  
|**source_object**|**sysname**|加入發行項的來源物件名稱。|  
|**description**|**nvarchar(255)**|發行項的描述。|  
|**destination_owner**|**sysname**|在訂閱者端建立的資料表之結構描述名稱。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表 &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
