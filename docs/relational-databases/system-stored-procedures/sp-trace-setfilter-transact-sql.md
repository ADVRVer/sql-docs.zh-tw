---
title: sp_trace_setfilter (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_trace_setfilter
- sp_trace_setfilter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_setfilter
ms.assetid: 11e7c7ac-a581-4a64-bb15-9272d5c1f7ac
caps.latest.revision: 35
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 64b40b4b7970db0252a873f6b3611d57672e3da0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sptracesetfilter-transact-sql"></a>sp_trace_setfilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  將篩選套用在追蹤上。 **sp_trace_setfilter**可能只能在已停止的現有追蹤上執行 (*狀態*是**0**)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如果追蹤不存在或其執行此預存程序會傳回錯誤*狀態*不**0**。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 請改用擴充事件。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_trace_setfilter [ @traceid = ] trace_id   
          , [ @columnid = ] column_id  
          , [ @logical_operator = ] logical_operator  
          , [ @comparison_operator = ] comparison_operator  
          , [ @value = ] value  
```  
  
## <a name="arguments"></a>引數  
 [ **@traceid=** ] *trace_id*  
 這是設定篩選的追蹤識別碼。 *trace_id*是**int**，沒有預設值。 使用者會利用這*trace_id*值來識別、 修改和控制追蹤。  
  
 [ **@columnid=** ] *column_id*  
 這是套用篩選的資料行識別碼。 *column_id*是**int**，沒有預設值。 如果*column_id*是 NULL，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]清除所有篩選器指定的追蹤。  
  
 [ **@logical_operator** = ] *logical_operator*  
 指定是否 AND (**0**) 或 OR (**1**) 運算子會套用。 *logical_operator*是**int**，沒有預設值。  
  
 [ **@comparison_operator=** ] *comparison_operator*  
 指定要進行的比較類型。 *comparison_operator*是**int**，沒有預設值。 這份資料表包含比較運算子及其代表值。  
  
|Value|比較運算子|  
|-----------|-------------------------|  
|**0**|= (等於)|  
|**1**|<> (不等於)|  
|**2**|> (大於)|  
|**3**|< (小於)|  
|**4**|>= (大於或等於)|  
|**5**|<= (小於或等於)|  
|**6**|LIKE|  
|**7**|不相似|  
  
 [  **@value=** ]*值*  
 指定要篩選的值。 資料型別*值*必須符合要篩選的資料行的資料類型。 例如，如果物件識別碼資料行上設定篩選**int**資料型別，*值*必須**int**。如果*值*是**nvarchar**或**varbinary**，它可以有最大長度為 8000。  
  
 當比較運算子是 LIKE 或 NOT LIKE 時，邏輯運算子可以併入 "%" 或 LIKE 運算所適用的其他篩選。  
  
 您可以指定 NULL*值*來篩選出具有 NULL 資料行值的事件。 只有**0** （= 等於） 和**1** (<> 不等於) 運算子是有效的 NULL。 在此情況下，這些運算子相當於 [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL 和 IS NOT NULL 運算子。  
  
 將篩選套用到資料行值的範圍之間**sp_trace_setfilter**必須執行兩次-一次更大-較-或-等於 ('> =') 比較運算子和另一次小於比-或-等於 ('< =') 運算子.  
  
 如需有關資料行資料類型的詳細資訊，請參閱[SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md)。  
  
## <a name="return-code-values"></a>傳回碼值  
 下表描述在預存程序完成之後，使用者可能得到的代碼值。  
  
|傳回碼|Description|  
|-----------------|-----------------|  
|0|沒有錯誤。|  
|1|未知的錯誤。|  
|2|追蹤目前在執行中。 此時變更追蹤會產生錯誤。|  
|4|指定的資料行無效。|  
|5|不允許指定的資料行進行篩選。 會傳回這個值只會從**sp_trace_setfilter**。|  
|6|指定的比較運算子無效。|  
|7|指定的邏輯運算子無效。|  
|9|指定的追蹤控制代碼無效。|  
|13|記憶體用完。 當沒有足夠的記憶體可以執行指定的動作時，便傳回這個代碼。|  
|16|函數對於這項追蹤無效。|  
  
## <a name="remarks"></a>備註  
 **sp_trace_setfilter**是[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]預存程序執行的許多較舊版本中提供的擴充預存程序由先前執行的動作[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 使用**sp_trace_setfilter**而不是**xp_trace_set\*篩選**擴充預存程序來建立、 套用、 移除或操作追蹤的篩選。 如需詳細資訊，請參閱[篩選追蹤](../../relational-databases/sql-trace/filter-a-trace.md)。  
  
 特定的資料行的所有篩選條件必須啟用一起執行一次**sp_trace_setfilter**。 例如，如果使用者想要在應用程式名稱資料行上套用兩個篩選，並在使用者名稱資料行上套用一個篩選，則使用者必須依序指定應用程式名稱的篩選。 如果使用者嘗試在一個預存程序呼叫中指定應用程式名稱的篩選，後面接著使用者名稱的篩選，以及應用程式名稱的另一個篩選，則 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會傳回錯誤。  
  
 參數的所有 SQL 追蹤預存程序 (**sp_trace_xx**) 都有強制類型。 如果沒有依照引數描述所指定，以正確的輸入參數資料類型來呼叫這些參數，預存程序會傳回錯誤。  
  
## <a name="permissions"></a>Permissions  
 使用者必須有 ALTER TRACE 權限。  
  
## <a name="examples"></a>範例  
 下列範例會在「追蹤 `1`」上設定三個篩選。 `N'SQLT%'` 和 `N'MS%'` 篩選會利用 "`AppName`" 比較運算子來處理一個資料行 (`10`，值是 `LIKE`)。 `N'joe'` 這個篩選利用 "`UserName`" 比較運算子來處理另一個資料行 (`11`，值是 `EQUAL`)。  
  
```  
sp_trace_setfilter  1, 10, 0, 6, N'SQLT%';  
sp_trace_setfilter  1, 10, 0, 6, N'MS%';  
sp_trace_setfilter  1, 11, 0, 0, N'joe';  
```  
  
## <a name="see-also"></a>另請參閱  
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [SQL 追蹤](../../relational-databases/sql-trace/sql-trace.md)  
  
  
