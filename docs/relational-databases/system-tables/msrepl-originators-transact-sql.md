---
description: MSrepl_originators (Transact-SQL)
title: MSrepl_originators (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_originators_TSQL
- MSrepl_originators
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_originators system table
ms.assetid: a3ac20a6-73f6-4fdc-ad5f-5f72746c9871
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 19e66da5cab574e18b592e0636cd9b3412870a10
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89544490"
---
# <a name="msrepl_originators-transact-sql"></a>MSrepl_originators (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MSrepl_originators**資料表針對產生交易的每個可更新訂閱者，各包含一個資料列。 這份資料表儲存在散發資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**id**|**int**|識別正在更新之訂閱者。|  
|**publisher_database_id**|**int**|識別發行集資料庫。|  
|**srvname**|**sysname**|正在更新之伺服器的名稱。|  
|**dbname**|**sysname**|正在更新之資料庫的名稱。|  
|**publication_id**|**int**|識別發行集。|  
|**dbversion]**|**int**|識別資料庫版本。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表 &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
