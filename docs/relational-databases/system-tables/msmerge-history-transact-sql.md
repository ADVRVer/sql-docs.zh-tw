---
title: MSmerge_history （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_history_TSQL
- MSmerge_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_history system table
ms.assetid: 936195ad-ca07-41a8-a1a0-6699b6e63403
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: de9c51e35bab142bd54a81224057f1eda05c5fb1
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829900"
---
# <a name="msmerge_history-transact-sql"></a>MSmerge_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_history**資料表包含歷程記錄資料列，其中含有先前合併代理程式作業會話之結果的詳細描述。 這份資料表會針對每一行代理程式輸出，各包含一個資料列。 這份資料表用於散發資料庫和每個訂閱資料庫中。 在散發資料庫中，它包含使用散發者之所有合併式發行集和訂閱的記錄。 在每個訂閱資料庫中，它包含訂閱者所訂閱之發行集的記錄。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|合併代理程式作業的識別碼。|  
|**agent_id**|**int**|合併代理程式的識別碼。|  
|**批註**|**nvarchar(255)**|訊息文字。|  
|**error_id**|**int**|[MSrepl_errors](../../relational-databases/system-tables/msrepl-errors-transact-sql.md)系統資料表中的錯誤識別碼。|  
|**timestamp**|**timestamp**|這份資料表的時間戳記資料行。|  
|**updatable_row**|**bit**|如果可以覆寫記錄資料列，則設定為**1** 。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表 &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
