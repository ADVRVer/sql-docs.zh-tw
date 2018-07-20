---
title: MStracer_tokens (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MStracer_tokens_TSQL
- MStracer_tokens
dev_langs:
- TSQL
helpviewer_keywords:
- MStracer_tokens system table
ms.assetid: b273aa48-8188-4213-8e2c-311543c3236f
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 25a5d05c3c4ad81da0856d4e073f7aeb462109e7
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103256"
---
# <a name="mstracertokens-transact-sql"></a>MStracer_tokens (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MStracer_tokens**資料表會維護追蹤插入發行集中的 token 記錄的記錄。 這份資料表儲存在散發資料庫中，並且由複寫用來監視效能之用。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**tracer_id**|**int**|識別追蹤 Token 記錄。|  
|**publication_id**|**int**|識別追蹤 Token 記錄所插入的發行集。|  
|**publisher_commit**|**datetime**|在發行者端認可追蹤 Token 記錄的日期和時間。|  
|**distributor_commit**|**datetime**|在散發者端認可追蹤 Token 記錄的日期和時間。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
