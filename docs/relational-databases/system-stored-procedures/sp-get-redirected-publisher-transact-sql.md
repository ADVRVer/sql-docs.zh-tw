---
title: sp_get_redirected_publisher (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/03/2017
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
- sp_get_redirected_publisher_TSQL
- sp_get_redirected_publisher
ms.assetid: d47a9ab5-f2cc-42a8-8be9-a33895ce44f0
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 28785969ea0bab2319d52461aa3e9a60f9be916d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32994985"
---
# <a name="spgetredirectedpublisher-transact-sql"></a>sp_get_redirected_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  複寫代理程式用來查詢散發者，以判斷原始發行者是否已經重新導向。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_get_redirected_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @bypass_publisher_validation = ] [0 | 1 ]  
```  
  
## <a name="arguments"></a>引數  
 [ **@original_publisher** =] **'***original_publisher***'**  
 要發行的資料庫名稱。 *publisher_db*是**sysname**，沒有預設值。  
  
 [ **@publisher_db** = ] **'***publisher_db***'**  
 要發行的資料庫名稱。 *publisher_db*是**sysname**，沒有預設值。  
  
 [ **@bypass_publisher_validation** = ] [0 | 1 ]  
 用來略過驗證重新導向的發行者。 如果為 0，則會執行驗證。 如果為 1，則不會執行驗證。 *bypass_publisher_validation*是**元**，預設值是 0。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**redirected_publisher**|**sysname**|重新導向之後的發行者名稱。|  
|**error_number**|**int**|驗證錯誤的錯誤號碼。|  
|**error_severity**|**int**|驗證錯誤的嚴重性。|  
|**error_message**|**nvarchar(4000)**|驗證錯誤訊息的文字。|  
  
## <a name="remarks"></a>備註  
 *redirected_publisher*傳回目前的發行者名稱。 如果發行者和發行資料庫沒有已重新導向使用會傳回 null **sp_redirect_publisher**。  
  
 如果未要求驗證，或項目不存在於發行者和發行資料庫， *error_number*和*error_severity*傳回 0 和*error_message*會傳回 null。  
  
 如果要求驗證，則驗證預存程序[sp_validate_redirected_publisher &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)呼叫以確認重新導向的目標是發行適合的主機資料庫。 如果驗證成功， **sp_get_redirected_publisher**傳回重新導向的發行者名稱，而 0 代表*error_number*和*error_severity*資料行和中的 null*error_message*資料行。  
  
 如果要求驗證而且失敗，則會傳回重新導向的發行者名稱以及錯誤資訊。  
  
## <a name="permissions"></a>Permissions  
 呼叫端必須是屬於**sysadmin**固定伺服器角色、 **db_owner**散發資料庫或定義的發行集的發行集存取清單成員的固定的資料庫角色與發行者資料庫相關聯。  
  
## <a name="see-also"></a>另請參閱  
 [複寫預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)   
 [sp_redirect_publisher &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
