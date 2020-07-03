---
title: MSpub_identity_range （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpub_identity_range_TSQL
- MSpub_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSpub_identity_range system table
ms.assetid: 68746eef-32e1-42bc-aff0-9798cd0e88b8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fb4ac1dbce35c3dd480e735581943d18f88094f3
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889604"
---
# <a name="mspub_identity_range-transact-sql"></a>MSpub_identity_range (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MSpub_identity_range**表提供識別範圍管理支援。 這份資料表儲存在發行集和訂閱資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**objid**|**int**|具有複寫所管理的識別欄位之資料表的識別碼。|  
|**range**|**bigint**|控制將在調整時，在訂閱進行指派的連續識別值的範圍大小。|  
|**pub_range**|**bigint**|控制將在調整時，在發行集進行指派的連續識別值的範圍大小。|  
|**current_pub_range**|**bigint**|發行集所用的目前範圍。 如果在**sp_changearticle**變更之後，以及在下一個範圍調整之前觀看，它可能會與*pub_range*不同。|  
|**threshold**|**int**|用來控制散發代理程式指派新識別範圍之時機的百分比值。 使用 [*臨界*值] 中指定的百分比時，散發代理程式會建立新的識別範圍。|  
|**last_seed**|**bigint**|目前範圍的下限。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表 &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
