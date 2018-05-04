---
title: sp_validate_redirected_publisher (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- sp_validate_redirected_publisher
- sp_validate_redirected_publisher_TSQL
helpviewer_keywords:
- sp_validate_redirected_publisher
ms.assetid: 2b7fdbad-17e4-4442-b0b2-9b5e8f84b91d
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: dd5fba573cd1a54a68087d5b1fd98f70a4e5ad7c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="spvalidateredirectedpublisher-transact-sql"></a>sp_validate_redirected_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  請確認發行之資料庫的目前主機是否能夠支援複寫。 必須從散發資料庫執行。 此程序會呼叫**sp_get_redirected_publisher**。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
      sp_validate_redirected_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @redirected_publisher = ] 'new_publisher' output  
```  
  
## <a name="arguments"></a>引數  
 [ **@original_publisher** =] **'***original_publisher***'**  
 當初發行資料庫的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱。 *original_publisher*是**sysname**，沒有預設值。  
  
 [ **@publisher_db** = ] **'***publisher_db***'**  
 要發行的資料庫名稱。 *publisher_db*是**sysname**，沒有預設值。  
  
 [ **@redirected_publisher** =] **'***redirected_publisher***'**  
 重新導向的目標時指定**sp_redirect_publisher**針對發行者/資料庫配對呼叫。 *redirected_publisher*是**sysname**，沒有預設值。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 無。  
  
## <a name="remarks"></a>備註  
 如果項目不存在於發行者和發行資料庫， **sp_validate_redirected_publisher**傳回輸出參數中的 null *@redirected_publisher*。 如果有項目存在，則成功和失敗案例的輸出參數中都會傳回此項目。  
  
 如果驗證成功， **sp_validate_redirected_publisher**傳回成功指示。  
  
 如果驗證失敗，則會引發描述失敗的錯誤。  
  
## <a name="permissions"></a>Permissions  
 呼叫端必須是屬於**sysadmin**固定伺服器角色、 **db_owner**散發資料庫或定義的發行集的發行集存取清單成員的固定的資料庫角色與發行者資料庫相關聯。  
  
## <a name="see-also"></a>另請參閱  
 [複寫預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_get_redirected_publisher &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_redirect_publisher &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
