---
title: sp_script_synctran_commands （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_script_synctran_commands
- sp_script_synctran_commands_TSQL
helpviewer_keywords:
- sp_script_synctran_commands
ms.assetid: f132694a-dd05-405b-9d84-21acce9e564a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 965fc3fe168ecd6027c2c1fc2ebad92bc334e383
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82816795"
---
# <a name="sp_script_synctran_commands-transact-sql"></a>sp_script_synctran_commands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  產生腳本，其中包含要在訂閱者端針對可更新訂閱套用的**sp_addsynctrigger**呼叫。 發行集中的每個發行項都有一個**sp_addsynctrigger**呼叫。 產生的腳本也會包含**sp_addqueued_artinfo**呼叫，以建立處理佇列發行集所需的**MSsubsciption_articles**資料表。 這個預存程序執行於發行集資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_script_synctran_commands [@publication = ] 'publication'  
    [ , [@article = ] 'article']  
```  
  
## <a name="arguments"></a>引數  
`[ @publication = ] 'publication'`這是要編寫腳本的發行集名稱。 *發行*集是**sysname**，沒有預設值。  
  
`[ @article = ] 'article'`這是要編寫腳本的發行項名稱。 發行項是**sysname**，預設值是**all**，指定所有發行項*都已編寫*腳本。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功）或**1** （失敗）  
  
## <a name="results-set"></a>結果集  
 **sp_script_synctran_commands**會傳回由單一**Nvarchar （4000）** 資料行所組成的結果集。 結果集會形成必要的完整腳本，以建立要在訂閱者端套用的**sp_addsynctrigger**和**sp_addqueued_artinfo**呼叫。  
  
## <a name="remarks"></a>備註  
 **sp_script_synctran_commands**用於快照式和異動複寫中。  
  
 **sp_addqueued_artinfo**用於已佇列的可更新訂閱。  
  
## <a name="permissions"></a>權限  
 只有**系統管理員（sysadmin** ）固定伺服器角色或**db_owner**固定資料庫角色的成員，才能夠執行**sp_script_synctran_commands**。  
  
## <a name="see-also"></a>另請參閱  
 [sp_addsynctriggers &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addsynctriggers-transact-sql.md)   
 [sp_addqueued_artinfo &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addqueued-artinfo-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
