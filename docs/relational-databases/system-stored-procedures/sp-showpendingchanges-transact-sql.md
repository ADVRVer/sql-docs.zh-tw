---
title: sp_showpendingchanges (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_showpendingchanges
- sp_showpendingchanges_TSQL
helpviewer_keywords:
- sp_showpendingchanges
ms.assetid: 8013a792-639d-4550-b262-e65d30f9d291
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2b59856ba83d3118a9246bb5cd93a8d63e7745f2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "33000735"
---
# <a name="spshowpendingchanges-transact-sql"></a>sp_showpendingchanges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回結果集，顯示正等候複寫的變更。 這個預存程序執行於發行集資料庫的發行者端，以及訂閱資料庫的訂閱者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
> [!NOTE]  
>  這個程序會提供變更數目的近似值，以及與這些變更相關的資料列。 例如，此程序會從發行者或訂閱者擷取資訊，但不會同時針對兩者進行。 儲存在另一個節點的資訊可能會使要同步處理的變更集比程序預估的變更集小。  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_showpendingchanges [ [ @destination_server = ] 'destination_server' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article']  
    [ , [ @show_rows = ] show_rows]  
```  
  
## <a name="arguments"></a>引數  
 [ @destination_server **=** ] **'***destination_server***'**  
 這是套用所複寫之變更的伺服器名稱。 *destination_server*是**sysname**，預設值是 NULL。  
  
 [ @publication **=** ] **'***發行集***'**  
 這是發行集的名稱。 *發行集*是**sysname**，預設值是 NULL。 當*發行集*指定，則結果只限於指定的發行集。  
  
 [ @article **=** ] **'***文章***'**  
 這是發行項的名稱。 *發行項*是**sysname**，預設值是 NULL。 當*文章*指定，則結果只限於指定的發行項。  
  
 [ @show_rows **=** ] *show_rows*  
 指定結果集是否包含更具體的資訊關於暫止的變更，預設值是**0**。 如果值為**1**指定，結果集包含資料行 is_delete 和 rowguid。  
  
## <a name="result-set"></a>結果集  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|destination_server|**sysname**|正要複寫變更所在的伺服器名稱。|  
|pub_name|**sysname**|發行集的名稱。|  
|destination_db_name|**sysname**|正要複寫變更所在的資料庫名稱。|  
|is_dest_subscriber|**bit**|指出正要將變更複寫到訂閱者。 值為**1**表示所做的變更複寫到訂閱者。 **0**表示變更複寫到發行者。|  
|article_name|**sysname**|引發變更之資料表的發行項名稱。|  
|pending_deletes|**int**|等候複寫的刪除數目。|  
|pending_ins_and_upd|**int**|等候複寫的插入和更新數目。|  
|is_delete|**bit**|表示暫止變更是否為刪除。 值為**1**表示變更為刪除。 需要的值為**1**如@show_rows。|  
|rowguid|**uniqueidentifier**|識別所變更之資料列的 GUID。 需要的值為**1**如@show_rows。|  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 sp_showpendingchanges 用於合併式複寫中。  
  
 sp_showpendingchanges 用於疑難排解合併式複寫之時。  
  
 sp_showpendingchanges 的結果並不包含層代 0 的資料列。  
  
 針對指定的發行項*文章*不屬於指定的發行集*發行集，* 對 pending_deletes 和 pending_ins_and_upd 傳回計數 0。  
  
## <a name="permissions"></a>Permissions  
 只有系統管理員 (sysadmin) 固定伺服器角色或 db_owner 固定資料庫角色的成員，才能夠執行 sp_showpendingchanges。  
  
## <a name="see-also"></a>另請參閱  
 [複寫預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
