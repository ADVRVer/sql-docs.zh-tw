---
title: MSmerge_identity_range_allocations （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_identity_range_allocations
- MSmerge_identity_range_allocations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range_allocations system table
ms.assetid: 6362e35e-0ab3-4638-855b-1ce013f5fd6d
author: stevestein
ms.author: sstein
ms.openlocfilehash: de0325925bb1ad1626987361435056ff21a26be6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68072652"
---
# <a name="msmerge_identity_range_allocations-transact-sql"></a>MSmerge_identity_range_allocations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_identity_range_allocations**資料表是用來針對已發行的發行項，追蹤識別範圍指派的歷程記錄和發行者和訂閱者。 這份資料表儲存在散發資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|發行者的識別碼。|  
|**publisher_db**|**nvarchar(128)**|發行集資料庫的名稱。|  
|**發行集**|**nvarchar(128)**|發行集的名稱。|  
|**篇**|**nvarchar(128)**|發行項的名稱。|  
|**預訂**|**nvarchar(128)**|訂閱者的名稱。|  
|**subscriber_db**|**nvarchar(128)**|訂閱資料庫的名稱。|  
|**is_pub_range**|**bit**|列出識別範圍是否被指派給發行者。|  
|**ranges_allocated**|**tinyint**|指派的識別範圍數。|  
|**range_begin**|**數位（38）**|範圍的起始值。|  
|**range_end**|**數位（38）**|範圍中的最後一值。|  
|**next_range_begin**|**數位（38）**|要指派之下一個範圍的起始值。|  
|**next_range_end**|**數位（38）**|要指派之下一個範圍的最後一個值。|  
|**max_used**|**數位（38）**|所用的最高識別值。|  
|**time_of_allocation**|**datetime**|指派的時間。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表 &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
