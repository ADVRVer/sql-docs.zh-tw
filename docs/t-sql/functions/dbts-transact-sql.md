---
title: '@@DBTS (Transact-SQL) | Microsoft Docs'
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@DBTS_TSQL'
- '@@DBTS'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@DBTS function'
- timestamp data type
ms.assetid: 91842ddd-91c0-4445-a03f-116f6bc991d0
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: fb455974db8eced1ec39c42a1013f0489965d630
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40dbts-transact-sql"></a>&#x40;&#x40;DBTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

傳回目前資料庫的目前 **timestamp** 資料類型值。 這個時間戳記在資料庫中必須是唯一的。
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>語法  
  
```
@@DBTS  
```  
  
## <a name="return-types"></a>傳回型別
**varbinary**
  
## <a name="remarks"></a>Remarks  
@@DBTS 會傳回前次使用的目前資料庫時間戳記值。 當您插入或更新含有 **timestamp** 資料行的資料列時，就會產生新的時間戳記值。
  
@@DBTS 函式不會受到交易隔離等級中的變更影響。
  
## <a name="examples"></a>範例  
下列範例會傳回 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 資料庫目前的 **timestamp**。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT @@DBTS;  
```  
  
## <a name="see-also"></a>另請參閱
[組態函式 &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)  
[資料指標並行 &#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/properties/cursor-concurrency-odbc.md)  
[資料類型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[MIN_ACTIVE_ROWVERSION &#40;Transact-SQL&#41;](../../t-sql/functions/min-active-rowversion-transact-sql.md)
  
  
