---
title: sp_rda_set_query_mode （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_query_mode
- sys.sp_rda_set_query_mode_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_query_mode stored procedure
ms.assetid: 65a0b390-cf87-4db7-972a-1fdf13456c88
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 98796b89486ce59b289c83a74e5c466a6522b557
ms.sourcegitcommit: 710d60e7974e2c4c52aebe36fceb6e2bbd52727c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2019
ms.locfileid: "72278320"
---
# <a name="syssp_rda_set_query_mode-transact-sql"></a>sys.sp_rda_set_query_mode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  指定是否針對目前已啟用 Stretch 的資料庫和其資料表的查詢同時傳回本機和遠端資料（預設值）或本機資料。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_rda_set_query_mode [ @mode = ] @mode   
    [ , [ @force = ]  @force ]  
```  
  
## <a name="arguments"></a>引數  
 [@mode =] *\@mode*  
 是下列其中一個值。  
  
-   **已停用**針對已啟用 Stretch 之資料表的所有查詢都會失敗。  
  
-   **LOCAL_ONLY**對已啟用 Stretch 之資料表的查詢只會傳回本機資料。  
  
-   **LOCAL_AND_REMOTE**針對已啟用 Stretch 之資料表的查詢會同時傳回本機和遠端資料。 這是預設行為。  
  
 [@force =] *\@force*  
 是選擇性的位值，如果您想要在沒有驗證的情況下變更查詢模式，您可以將它設定為1。  
  
## <a name="return-code-values"></a>傳回碼值  
 0（成功）或 > 0 （失敗）  
  
## <a name="permissions"></a>Permissions  
 需要 db_owner 許可權。  
  
## <a name="remarks"></a>備註  
 下列擴充預存程式也會針對已啟用延展功能的資料庫設定查詢模式。  
  
-   **sp_rda_deauthorize_db**  
  
     執行**sp_rda_deauthorize_db**之後，針對已啟用 Stretch 的資料庫和資料表的所有查詢都會失敗。 也就是，查詢模式設定為 [停用]。 若要結束此模式，請執行下列其中一項動作。  
  
    -   執行[sp_rda_reauthorize_db &#40;transact-sql&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md)以重新連接到遠端 Azure 資料庫。 此操作會自動將查詢模式重設為 LOCAL_AND_REMOTE，這是 Stretch Database 的預設行為。 也就是說，查詢會傳回本機和遠端資料的結果。  
  
    -   使用 LOCAL_ONLY 引數執行[sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) ，讓查詢只會針對本機資料執行。  
  
-   **sp_rda_reauthorize_db**  
  
     當您執行[sp_rda_reauthorize_db &#40;transact-sql&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md)以重新連接到遠端 Azure 資料庫時，此作業會自動將查詢模式重設為 LOCAL_AND_REMOTE，這是 Stretch Database 的預設行為。 也就是說，查詢會傳回本機和遠端資料的結果。  
  
## <a name="see-also"></a>另請參閱  
 [sys.sp_rda_deauthorize_db &#40;SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
