---
title: sp_register_custom_scripting （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_register_custom_scripting
- sp_register_custom_scripting_TSQL
helpviewer_keywords:
- sp_register_custom_scripting
ms.assetid: a8159282-de3b-4b9e-bdc9-3d3fce485c7f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 80736db0e2356d3592744393ff8964ac6f6073c0
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85891498"
---
# <a name="sp_register_custom_scripting-transact-sql"></a>sp_register_custom_scripting (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  複寫可讓使用者自訂的自訂預存程序，取代異動複寫所用的一個或多個預設程序。 當複寫資料表變更結構描述時，就會重新建立這些預存程序。 **sp_register_custom_scripting**註冊一個預存 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式或腳本檔案，該檔案會在發生架構變更時執行，以編寫新使用者定義自訂預存程式的定義腳本。 這個新的使用者自訂之自訂預存程序，應該要反映該資料表的新結構描述。 **sp_register_custom_scripting**是在發行集資料庫的發行者端執行，而註冊的腳本檔案或預存程式則是在發生架構變更時于訂閱者端執行。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_register_custom_scripting [ @type  = ] 'type'  
    [ @value = ] 'value'   
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @type = ] 'type'`這是要註冊之自訂預存程式或腳本的類型。 *類型*為**Varchar （16）**，沒有預設值，而且可以是下列其中一個值。  
  
|值|說明|  
|-----------|-----------------|  
|**插入**|註冊的自訂預存程序是在複寫 INSERT 陳述式時執行。|  
|**update**|註冊的自訂預存程序是在複寫 UPDATE 陳述式時執行。|  
|**delete**|註冊的自訂預存程序是在複寫 DELETE 陳述式時執行。|  
|**custom_script**|指令碼是在資料定義語言 (DDL) 觸發程序結尾執行。|  
  
`[ @value = ] 'value'`預存程式的名稱，或是要註冊之腳本檔案的名稱和完整路徑 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。 *value*是**Nvarchar （1024）**，沒有預設值。  
  
> [!NOTE]  
>  為*value*參數指定 Null 將會取消註冊先前註冊的腳本，這與執行[sp_unregister_custom_scripting](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md)相同。  
  
 當*類型*的值是**custom_script**時，就應該要有腳本檔案的名稱和完整路徑 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。 否則， *value*必須是已註冊之預存程式的名稱。  
  
`[ @publication = ] 'publication'`要註冊其自訂預存程式或腳本的發行集名稱。 *發行*集是**sysname**，預設值是**Null**。  
  
`[ @article = ] 'article'`要為其註冊自訂預存程式或腳本的發行項名稱。 發行*項是* **sysname**，預設值是**Null**。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功）或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_register_custom_scripting**用於快照式和異動複寫中。  
  
 在變更複寫資料表的結構描述之前，要先執行這個預存程序。 如需使用這個預存程式的詳細資訊，請參閱[重新產生自訂交易程式以反映架構變更](../../relational-databases/replication/transactional/transactional-articles-regenerate-to-reflect-schema-changes.md)。  
  
## <a name="permissions"></a>權限  
 只有**系統管理員（sysadmin** ）固定伺服器角色、 **db_owner**固定資料庫角色或**db_ddladmin**固定資料庫角色的成員，才能夠執行**sp_register_custom_scripting**。  
  
## <a name="see-also"></a>另請參閱  
 [sp_unregister_custom_scripting &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md)  
  
  
