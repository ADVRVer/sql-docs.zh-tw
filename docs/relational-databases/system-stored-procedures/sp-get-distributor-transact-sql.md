---
description: sp_get_distributor (Transact-SQL)
title: sp_get_distributor (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_get_distributor
- sp_get_distributor_TSQL
helpviewer_keywords:
- sp_get_distributor
ms.assetid: f0134448-bc17-4f2f-bd81-619351ce56ac
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 737437b6bdd3de8b0d261345de47bad4fdf55eea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447103"
---
# <a name="sp_get_distributor-transact-sql"></a>sp_get_distributor (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  判斷散發者是否安裝在伺服器中。 這個預存程序執行於任何資料庫中散發者所在的電腦。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_get_distributor   
```  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**安裝**|**int**|**0** = 否; **1** = 是|  
|**散發伺服器**|**sysname**|散發者伺服器的名稱|  
|**已安裝散發資料庫**|**int**|**0** = 否; **1** = 是|  
|**is distribution publisher**|**int**|**0** = 否; **1** = 是|  
|**具有遠端散發發行者**|**int**|**0** = 否; **1** = 是|  
  
## <a name="remarks"></a>備註  
 **sp_get_distributor** [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在快照式、交易式和合併式複寫中，主要會使用 sp_get_distributor。  
  
## <a name="permissions"></a>權限  
 任何使用者都可以執行 **sp_get_distributor**。 當這個預存程式是由散發資料庫上的 **db_owner** 或 **replmonitor** 固定資料庫角色的成員，或是至少一個已發行資料庫上 **db_owner** 固定資料庫角色的成員執行時，就會傳回非 Null 結果集。 當發行集存取清單中的使用者執行此預存程式時，也會傳回非 Null 結果集 (PAL) 至少一個已發行的資料庫，或非 SQL Server 發行者的散發資料庫 PAL 中，也可以執行 **sp_get_distributor**。  
  
## <a name="see-also"></a>另請參閱  
 [設定發行和散發](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [散發者與發行者資訊指令碼](../../relational-databases/replication/administration/distributor-and-publisher-information-script.md)   
 [複寫預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
