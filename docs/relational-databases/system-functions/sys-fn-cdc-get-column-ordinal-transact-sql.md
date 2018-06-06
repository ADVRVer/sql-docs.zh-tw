---
title: sys.fn_cdc_get_column_ordinal (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 01/25/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
f1_keywords:
- sys.fn_cdc_get_column_ordinal
- fn_cdc_get_column_ordinal_TSQL
- fn_cdc_get_column_ordinal
- sys.fn_cdc_get_column_ordinal_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_get_column_ordinal
- sys.fn_cdc_get_column_ordinal
ms.assetid: 4bb21a57-2b94-4208-8bdf-6a3e2681d881
caps.latest.revision: 16
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 70ca20e98ba1330482fd19265b7f54f07d9711e4
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="sysfncdcgetcolumnordinal-transact-sql"></a>sys.fn_cdc_get_column_ordinal (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回指定的資料行，因為它的資料行序數會出現在[變更資料表](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)指定的擷取執行個體相關聯。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sys.fn_cdc_get_column_ordinal ( 'capture_instance','column_name')  
```  
  
## <a name="arguments"></a>引數  
 **'** *capture_instance* **'**  
 這是指定資料行識別為已擷取資料行之擷取執行個體的名稱。 *capture_instance*是**sysname**。  
  
 **'** *column_name* **'**  
 這是要回報的資料行。 *column_name*是**sysname**。  
  
## <a name="return-type"></a>傳回類型  
 **int**  
  
## <a name="remarks"></a>備註  
 這個函數是用來識別擷取資料行在異動資料擷取更新遮罩中的序數位置。 主要用於搭配函數[sys.fn_cdc_is_bit_set](../../relational-databases/system-functions/sys-fn-cdc-is-bit-set-transact-sql.md)查詢變更資料時，從更新遮罩中擷取資訊。  
  
## <a name="permissions"></a>Permissions  
 需要來源資料表之所有擷取資料行的 SELECT 權限。 如果已針對擷取執行個體指定了異動資料擷取元件的資料庫角色，也會需要該角色的成員資格。  
  
## <a name="examples"></a>範例  
 下列範例會取得 `VacationHours` 資料行在 `HumanResources_Employee` 擷取執行個體之更新遮罩中的序數位置。 然後，該值會用於 `sys.fn_cdc_is_bit_set` 的呼叫中，以便從傳回的更新遮罩中擷取資訊。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @from_lsn binary(10), @to_lsn binary(10),  @VacationHoursOrdinal int;  
SET @from_lsn = sys.fn_cdc_get_min_lsn('HumanResources_Employee');  
SET @to_lsn = sys.fn_cdc_get_max_lsn();  
SET @VacationHoursOrdinal = sys.fn_cdc_get_column_ordinal   
    ( 'HumanResources_Employee','VacationHours');  
SELECT *, sys.fn_cdc_is_bit_set(@VacationHoursOrdinal,  
    __$update_mask) as 'VacationHours'  
FROM cdc.fn_cdc_get_net_changes_HumanResources_Employee  
    ( @from_lsn, @to_lsn, 'all with mask');  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [異動資料擷取函數 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-data-capture-functions-transact-sql.md)   
 [關於異動資料擷取 &#40;SQL Server &#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)   
 [sys.sp_cdc_help_change_data_capture &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [sys.sp_cdc_get_captured_columns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-captured-columns-transact-sql.md)   
 [sys.fn_cdc_is_bit_set &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-is-bit-set-transact-sql.md)  
  
  
