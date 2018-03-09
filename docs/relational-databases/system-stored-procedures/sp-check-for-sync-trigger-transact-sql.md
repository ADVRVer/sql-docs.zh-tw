---
title: "sp_check_for_sync_trigger (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- filter_TSQL
- sp_check_for_sync_trigger
helpviewer_keywords:
- sp_check_for_sync_trigger
ms.assetid: 54a1e2fd-c40a-43d4-ac64-baed28ae4637
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 586498365ee695ee5dc92252af47ad7706e1adfb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="spcheckforsynctrigger-transact-sql"></a>sp_check_for_sync_trigger (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  決定是否要在立即更新訂閱所使用的複寫觸發程序內容中呼叫使用者自訂觸發程序或是預存程序。 這個預存程序執行於發行集資料庫的發行者端，或訂閱資料庫的訂閱者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_check_for_sync_trigger [ @tabid = ] 'tabid'   
    [ , [ @trigger_op = ] 'trigger_output_parameters' OUTPUT ]  
    [ , [ @fonpublisher = ] fonpublisher ]  
```  
  
## <a name="arguments"></a>引數  
 [ **@tabid =** ] '*tabid*'  
 這是要檢查立即更新觸發程序之資料表的物件識別碼。 *tabid*是**int**沒有預設值。  
  
 [ **@trigger_op =** ] '*trigger_output_parameters*' 輸出  
 指定輸出參數是否要傳回呼叫它之觸發程序的類型。 *trigger_output_parameters*是**char （10)**而且可以是下列值之一。  
  
|值|Description|  
|-----------|-----------------|  
|**集**|INSERT 觸發程序|  
|**Upd**|UPDATE 觸發程序|  
|**Del**|DELETE 觸發程序|  
|NULL (預設值)||  
  
 [  **@fonpublisher =** ] *fonpublisher*  
 指定預存程序執行所在位置。 *fonpublisher*是**元**，預設值為 0。 如果為 0，則是在訂閱者端執行，如果為 1，則是在發行者端執行。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 表示並非在立即更新觸發程序的內容中呼叫預存程序。 1 表示它一個立即更新觸發程序的內容中被呼叫，而是觸發程序中所傳回的型別 *@trigger_op* 。  
  
## <a name="remarks"></a>備註  
 **sp_check_for_sync_trigger**用於快照式複寫和異動複寫。  
  
 **sp_check_for_sync_trigger**用來協調複寫和使用者定義的觸發程序。 這個預存程序會判斷它是否在複寫觸發程序內容之內受到呼叫。 例如，您可以呼叫此程序**sp_check_for_sync_trigger**使用者定義的觸發程序主體中。 如果**sp_check_for_sync_trigger**傳回**0**，使用者定義的觸發程序會繼續處理。 如果**sp_check_for_sync_trigger**傳回**1**，使用者定義的觸發程序會結束。 這可以確定當複寫觸發程序更新資料表時，不會引發使用者自訂觸發程序。  
  
## <a name="example"></a>範例  
 下列範例會顯示可用於訂閱者資料表之觸發程序中的程式碼。  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int  
SELECT @table_id = object_id('tablename')  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT  
IF @retcode = 1  
RETURN  
```  
  
## <a name="example"></a>範例  
 在發行者端; 在資料表上的觸發程序也可以加入的程式碼程式碼很類似，但呼叫**sp_check_for_sync_trigger**包含其他參數。  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int, @fonpublisher int  
SELECT @table_id = object_id('tablename')  
SELECT @fonpublisher = 1  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT, @fonpublisher  
IF @retcode = 1  
RETURN  
```  
  
## <a name="permissions"></a>Permissions  
 **sp_check_for_sync_trigger**具有 SELECT 權限中的任何使用者可以執行預存程序[sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)系統檢視表。  
  
## <a name="see-also"></a>請參閱＜  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
