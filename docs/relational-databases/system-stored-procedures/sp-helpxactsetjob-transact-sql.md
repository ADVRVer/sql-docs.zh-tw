---
title: sp_helpxactsetjob (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpxactsetjob
- sp_helpxactsetjob_TSQL
helpviewer_keywords:
- sp_helpxactsetjob
ms.assetid: 242cea3e-e6ac-4f84-a072-b003b920eb33
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5bcea94b8d7e83d74ee9295658943ac41c619628
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpxactsetjob-transact-sql"></a>sp_helpxactsetjob (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  顯示 Oracle 發行者的 Xactset 作業的相關資訊。 這個預存程序執行於任何資料庫中的散發者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helpxactsetjob [ @publisher = ] 'publisher'   
```  
  
## <a name="arguments"></a>引數  
 [**@publisher** =] **'***發行者***'**  
 這是作業所屬的非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 發行者名稱。 *發行者*是**sysname**，沒有預設值。  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**jobnumber**|**int**|Oracle 作業編號。|  
|**lastdate**|**varchar(22)**|上次作業執行的日期。|  
|**thisdate**|**varchar(22)**|變更的時間|  
|**nextdate**|**varchar(22)**|下次作業執行的日期。|  
|**中斷**|**varchar(1)**|指出作業是否中斷的旗標。|  
|**間隔**|**varchar(200)**|作業的間隔時間。|  
|**失敗**|**int**|作業的失敗次數。|  
|**xactsetjobwhat**|**varchar(200)**|作業所執行的程序名稱。|  
|**xactsetjob**|**varchar(1)**|作業的狀態，它可以是下列項目之一：<br /><br /> **1** -作業已啟用。<br /><br /> **0** -作業已停用。|  
|**xactsetlonginterval**|**int**|作業的長間隔時間。|  
|**xactsetlongthreshold**|**int**|作業的長臨界值。|  
|**xactsetshortinterval**|**int**|作業的短間隔時間。|  
|**xactsetshortthreshold**|**int**|作業的短臨界值。|  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_helpxactsetjob**用於快照式複寫和異動複寫，Oracle 發行者。  
  
 **sp_helpxactsetjob**一律會傳回在發行者端的 Xactset 作業 (HREPL_XactSetJob) 的目前設定。 如果 Xactset 作業目前在作業佇列中，還會另外從以 Oracle 發行者管理員帳戶建立的 USER_JOB 資料字典檢視，傳回作業屬性。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色可以執行**sp_helpxactsetjob**。  
  
## <a name="see-also"></a>另請參閱  
 [設定 Oracle 發行者的交易集作業 &#40;複寫 Transact-SQL 程式設計&#41;](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
 [sp_publisherproperty &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)  
  
  
