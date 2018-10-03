---
title: sys.fn_cdc_has_column_changed (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_cdc_has_column_changed_TSQL
- sys.fn_cdc_has_column_changed
- fn_cdc_has_column_changed_TSQL
- fn_cdc_has_column_changed
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_cdc_has_column_changed
- fn_cdc_has_column_changed
ms.assetid: 2b9e6278-050d-4ffc-8d1a-09606180facc
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3d3df1bd07e73c3c363a0fd275e910c3c32cbe71
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645176"
---
# <a name="sysfncdchascolumnchanged-transact-sql"></a>sys.fn_cdc_has_column_changed (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  識別指定的更新遮罩是否表示指定的資料行已經在相關聯的變更資料列中更新。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sys.fn_cdc_has_column_changed ( 'capture_instance','column_name' , update_mask )  
```  
  
## <a name="arguments"></a>引數  
 **'** *capture_instance* **'**  
 這是擷取執行個體的名稱。 *capture_instance*已**sysname**。  
  
 **'** *column_name* **'**  
 這是要回報之指定擷取執行個體的擷取資料行。 *column_name*已**sysname**。  
  
 *update_mask*  
 這是在任何相關聯變更資料列中識別已更新資料行的遮罩。 *update_mask*已**varbinary(128)**。  
  
## <a name="return-type"></a>傳回類型  
 **bit**  
  
## <a name="remarks"></a>備註  
 您可以使用這個函數，從在查詢變更資料時傳回的更新遮罩中擷取資訊。 當您需要知道相關聯變更資料列中的特定資料行是否已經修改時，這在後置處理更新遮罩中最有用。 如需詳細資訊，請參閱[關於異動資料擷取 &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)。  
  
 當變更資料查詢的一部分，就會傳回這項資訊時，我們建議您使用函數[sys.fn_cdc_get_column_ordinal](../../relational-databases/system-functions/sys-fn-cdc-get-column-ordinal-transact-sql.md)並[sys.fn_cdc_is_bit_set](../../relational-databases/system-functions/sys-fn-cdc-is-bit-set-transact-sql.md)而不是此函式。 請在查詢變更資料之前使用 fn_cdc_get_column_ordinal 函數，以便僅計算一次所需的資料行序數。 您可以在查詢中使用 fn_cdc_is_bit_set，以便針對每個傳回的資料列從更新遮罩中擷取資訊。  
  
## <a name="permissions"></a>Permissions  
 需要系統管理員 (sysadmin) 固定伺服器角色或 db_owner 固定資料庫角色中的成員資格。 若為所有其他使用者，則需要來源資料表中所有擷取資料行的 SELECT 權限，而且如果定義了擷取執行個體的控制角色，便需要該資料庫角色的成員資格。  
  
## <a name="see-also"></a>另請參閱  
 [cdc。&#60;capture_instance&#62;_CT &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)   
 [cdc.captured_columns &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-tables/cdc-captured-columns-transact-sql.md)  
  
  
