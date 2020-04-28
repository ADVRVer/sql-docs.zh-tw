---
title: sysusers （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysusers
- sys.sysusers_TSQL
- sysusers_TSQL
- sysusers
dev_langs:
- TSQL
helpviewer_keywords:
- sysusers system table
- sys.sysusers compatibility view
ms.assetid: 5f0e6a8d-c983-44f6-97e9-aab5bff67d18
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1b8bec28a2e7778a449cb36aeee81481a311c6b9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "68018070"
---
# <a name="syssysusers-transact-sql"></a>sys.sysusers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  針對資料庫中的每[!INCLUDE[msCoName](../../includes/msconame-md.md)]個 windows 使用者、windows 群組[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、使用者或[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]角色，各包含一個資料列。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**uid**|**smallint**|使用者識別碼，在這個資料庫中是唯一的。<br /><br /> 1 = 資料庫擁有者<br /><br /> 如果使用者和角色數目超過 32,767 個，則會造成溢位或傳回 NULL。|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**name**|**sysname**|使用者名稱或群組名稱，在這個資料庫中是唯一的。|  
|**sid**|**Varbinary （85）**|這個項目的安全性識別碼。|  
|**角色**|**varbinary(2048)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**createdate**|**datetime**|加入帳戶的日期。|  
|**updatedate**|**datetime**|上次變更帳戶的日期。|  
|**altuid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> 如果使用者和角色數目超過 32,767 個，則會造成溢位或傳回 NULL。|  
|**password**|**varbinary(256)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**gid**|**smallint**|這位使用者所屬的群組識別碼。 如果**uid**與**gid**相同，此專案會定義一個群組。 如果群組和使用者結合的數目超過 32,767，則會造成溢位或傳回 NULL。|  
|**environ**|**varchar(255)**|已保留。|  
|**hasdbaccess**|**int**|1 = 帳戶有資料庫存取權。|  
|**islogin**|**int**|1 = 帳戶是具有登入帳戶的 Windows 群組、Windows 使用者或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者。|  
|**isntname**|**int**|1 = 帳戶是 Windows 群組或 Windows 使用者。|  
|**isntgroup**|**int**|1 = 帳戶是 Windows 群組。|  
|**isntuser**|**int**|1 = 帳戶是 Windows 使用者。|  
|**issqluser**|**int**|1 = 帳戶是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者。|  
|**isaliased**|**int**|1 = 帳戶是另一位使用者的別名。|  
|**issqlrole**|**int**|1 = 帳戶是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 角色。|  
|**isapprole**|**int**|1 = 帳戶是應用程式角色。|  
  
## <a name="see-also"></a>另請參閱  
 [將系統資料表對應至系統檢視 &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [相容性檢視 &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
