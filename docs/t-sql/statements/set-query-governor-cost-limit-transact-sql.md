---
title: SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SET QUERY_GOVERNOR_COST_LIMIT
- SET_QUERY_GOVERNOR_COST_LIMIT_TSQL
- QUERY_GOVERNOR_COST_LIMIT
- QUERY_GOVERNOR_COST_LIMIT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET QUERY_GOVERNOR_COST_LIMIT statement
- connections [SQL Server], overriding
- QUERY_GOVERNOR_COST_LIMIT option
- overriding connection values
ms.assetid: 3424bb44-6915-462d-a8d7-fe834af81387
caps.latest.revision: 27
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 333d04c02e9159b475920bc7af8b37b46a37a393
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/04/2018
ms.locfileid: "37786199"
---
# <a name="set-querygovernorcostlimit-transact-sql"></a>SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  覆寫目前針對目前連接所設定的**查詢管理員成本限制值**。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
SET QUERY_GOVERNOR_COST_LIMIT value  
```  
  
## <a name="arguments"></a>引數  
 *value*  
 這是指定查詢可以執行的最長時間之數值或整數值。 值會捨到最接近的整數。 負值會進位到 0。 查詢若超過該值的估計成本，查詢管理員就不允許執行此查詢。 將這個選項指定為 0 (預設值) 會關閉查詢管理員，並允許無限期地執行所有查詢。  
  
 「查詢成本」代表在特定的硬體組態上，預估完成查詢所需的時間 (以秒為單位)。  
  
## <a name="remarks"></a>Remarks  
 使用 SET QUERY_GOVERNOR_COST_LIMIT 只適用於目前的連接，在目前連接的期間會持續有效。 請利用 **sp_configure** 的[設定查詢管理員成本限制伺服器組態選項](../../database-engine/configure-windows/configure-the-query-governor-cost-limit-server-configuration-option.md)選項來變更伺服器範圍的查詢管理員成本限制值。 如需有關設定這個選項的詳細資訊，請參閱 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) 和[伺服器組態選項 &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)。  
  
 SET QUERY_GOVERNOR_COST_LIMIT 的設定是在執行階段進行設定，而不是在剖析階段進行設定。  
  
## <a name="permissions"></a>Permissions  
 需要 **public** 角色的成員資格。  
  
## <a name="see-also"></a>另請參閱  
 [SET 陳述式 &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
