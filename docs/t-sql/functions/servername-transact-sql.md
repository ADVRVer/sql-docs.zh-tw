---
title: "@@SERVERNAME (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 09/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@SERVERNAME'
- '@@SERVERNAME_TSQL'
dev_langs: TSQL
helpviewer_keywords:
- '@@SERVERNAME function'
- local servers [SQL Server]
ms.assetid: b0ef33fb-954a-4294-b05b-a87c14ce25a3
caps.latest.revision: "34"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 5f1e7dbd47562368653ce75eee9d2a412164a9c9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40servername-transact-sql"></a>&#x40;&#x40;SERVERNAME (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回本機伺服器執行名稱[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
@@SERVERNAME  
```  
  
## <a name="return-types"></a>傳回類型  
 **nvarchar**  
  
## <a name="remarks"></a>備註  
 在安裝期間，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式會將伺服器名稱設成電腦名稱。 若要變更伺服器的名稱，請使用**sp_addserver**，然後重新啟動[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
 多個執行個體的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]安裝時，@@SERVERNAME傳回下列本機伺服器名稱資訊，如果未安裝之後變更本機伺服器名稱。  
  
|執行個體|伺服器資訊|  
|--------------|------------------------|  
|預設執行個體|'*servername*'|  
|具名執行個體|'*servername*\\*instancename*'|  
|容錯移轉叢集執行個體 - 預設執行個體|'*virtualservername*'|  
|容錯移轉叢集執行個體 - 具名執行個體|'*virtualservername*\\*instancename*'|  
  
 雖然 @@SERVERNAME函式和 SERVERPROPERTY 函數的 SERVERNAME 屬性可能會傳回有類似格式的字串，資訊可能會不同。 SERVERNAME 屬性會自動報告電腦網路名稱的變更。  
  
 相反地，@@SERVERNAME不會報告這類變更。 @@SERVERNAME報告本機伺服器名稱使用所做的變更 **sp_addserver** 或 **sp_dropserver** 預存程序。  
  
## <a name="examples"></a>範例  
 下列範例會顯示如何使用 `@@SERVERNAME`。  
  
```  
SELECT @@SERVERNAME AS 'Server Name'  
```  
  
 範例結果集如下：  
  
```  
Server Name  
---------------------------------  
ACCTG  
  
```  
  
## <a name="see-also"></a>請參閱＜  
 [組態函式 &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
 [sp_addserver &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)  
  
  
