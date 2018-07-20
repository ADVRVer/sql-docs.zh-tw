---
title: MSmerge_metadataaction_request (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
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
- MSmerge_metadataaction_request
- MSmerge_metadataaction_request_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_metadataaction_request system table
ms.assetid: cd31a114-900a-4218-ab58-d959e547c647
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 951b42bb78d2b15d2d107e6a4de0291aa16c7693
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103226"
---
# <a name="msmergemetadataactionrequest-transact-sql"></a>MSmerge_metadataaction_request (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_metadataaction_request**資料表會儲存每個補償動作所需的一個資料列。 如果發生錯誤，且必須重試同步處理，請使用 Web 同步處理，項目會變成**MSmerge_metadataaction_request**。 在進行後續合併的上傳階段時，對於所有屬於正在同步處理之發行集的發行項要求，都是從這份資料表擷取及上傳。 當同步處理成功完成時，在對應的資料列**MSmerge_metadataaction_request**刪除資料表。 這份資料表儲存在發行集資料庫的發行者端，以及訂閱資料庫的訂閱者端。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|已發行資料表的暱稱。|  
|**rowguid**|**uniqueidentifier**|給定資料列的資料列識別碼。|  
|**action**|**tinyint**|識別必要的補償動作。|  
|**產生**|**bigint**|必須進行補償動作的產生值。|  
|**變更**|**int**|僅供內部使用。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視&#40;Transact SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [合併式複寫的 Web 同步處理](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
