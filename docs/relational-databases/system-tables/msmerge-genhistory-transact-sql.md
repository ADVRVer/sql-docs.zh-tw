---
title: MSmerge_genhistory (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_genhistory_TSQL
- MSmerge_genhistory
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_genhistory system table
ms.assetid: 475d08ae-eb8b-49de-afd6-33c96ab8004d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d57447c1e7beeb29da3a39517e1cb5b84f0b32f9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692356"
---
# <a name="msmergegenhistory-transact-sql"></a>MSmerge_genhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_genhistory**資料表包含一個資料列的訂閱者 （在保留期限內） 知道每個層代。 其目的是防止在交換時傳送共用層代 (Generation)，並且重新同步處理從備份還原的訂閱者。 這份資料表儲存在發行集和訂閱資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**guidsrc**|**uniqueidentifier**|由訂閱者的層代 (Generation) 所識別之變更的全域識別碼。|  
|**pubid**|**uniqueidentifier**|發行集識別碼。|  
|**產生**|**bigint**|層代 (Generation) 值。|  
|**art_nick**|**int**|發行項的暱稱。|  
|**暱稱**|**varbinary(1001)**|這個層代 (Generation) 已經知道的其他訂閱者的暱稱清單。 其目的是避免將層代 (Generation) 傳送給已經看過那些變更的訂閱者。 為了提高搜尋的效率，暱稱清單中的暱稱都是依序維護的。 如果暱稱太多，超過這個欄位的容量，它們就無法達到最佳化的效果。|  
|**coldate**|**datetime**|將目前層代 (Generation) 加入資料表中的日期。|  
|**層代狀態**|**tinyint**|層代 (Generation) 狀態如下：<br /><br /> **0** = 已開啟。<br /><br /> **1** = 關閉。<br /><br /> **2** = 已關閉，以及引發另一個訂閱者端。|  
|**changecount**|**int**|在給定層代 (Generation) 反映的變更數目|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
