---
title: sp_getdefaultdatatypemapping (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_getdefaultdatatypemapping_TSQL
- sp_getdefaultdatatypemapping
helpviewer_keywords:
- sp_getdefaultdatatypemapping
ms.assetid: b8401de1-f135-41d0-ba79-ce8fe1f48c00
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2559c69e5857bbc5796d68d19b7d760476594b87
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2018
ms.locfileid: "53589192"
---
# <a name="spgetdefaultdatatypemapping-transact-sql"></a>sp_getdefaultdatatypemapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回指定的資料類型之間的預設對應的相關資訊[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]與非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料庫管理系統 (DBMS)。 這個預存程序執行於任何資料庫中的散發者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_getdefaultdatatypemapping [ @source_dbms = ] 'source_dbms'   
    [ , [ @source_version = ] 'source_version' ]  
        , [ @source_type = ] 'source_type'    
    [ , [ @source_length = ] source_length ]  
    [ , [ @source_precision = ] source_precision ]  
    [ , [ @source_scale = ] source_scale ]  
    [ , [ @source_nullable = ] source_nullable ]  
        , [ @destination_dbms = ] 'destination_dbms'   
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' OUTPUT ]  
    [ , [ @destination_length = ] destination_length OUTPUT ]  
    [ , [ @destination_precision = ] destination_precision OUTPUT ]  
    [ , [ @destination_scale = ] destination_scale OUTPUT ]  
    [ , [ @destination_nullable = ] source_nullable OUTPUT ]  
    [ , [ @dataloss = ] dataloss OUTPUT ]  
```  
  
## <a name="arguments"></a>引數  
 [ **@source_dbms**=] **'**_source_dbms_**'**  
 這是對應資料類型的來源 DBMS 名稱。 *source_dbms*已**sysname**，而且可以是下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|**MSSQLSERVER**|來源是一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。|  
|**ORACLE**|來源是一個 Oracle 資料庫。|  
  
 您必須指定這個參數。  
  
 [  **@source_version=** ] **'**_source_version_**'**  
 這是來源 DBMS 的版本號碼。 *source_version*已**varchar(10)**，預設值是 NULL。  
  
 [ **@source_type**=] **'**_source_type_**'**  
 這是來源 DBMS 中的資料類型。 *source_type*已**sysname**，沒有預設值。  
  
 [  **@source_length=** ] *source_length*  
 這是來源 DBMS 的資料類型長度。 *source_length*已**bigint**，預設值是 NULL。  
  
 [  **@source_precision=** ] *source_precision*  
 這是來源 DBMS 之資料類型的有效位數。 *source_precision*已**bigint**，預設值是 NULL。  
  
 [  **@source_scale=** ] *source_scale*  
 這是來源 DBMS 中的資料類型的小數位數。 *source_scale*已**int**，預設值是 NULL。  
  
 [  **@source_nullable=** ] *source_nullable*  
 這是指來源 DBMS 中的資料類型是否支援 NULL 值。 *source_nullable*已**位元**，預設值是**1**，這表示支援 NULL 值。  
  
 [ **@destination_dbms** =] **'**_destination_dbms_**'**  
 這是目的地 DBMS 的名稱。 *destination_dbms*已**sysname**，而且可以是下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|**MSSQLSERVER**|目的地是一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。|  
|**ORACLE**|目的地是一個 Oracle 資料庫。|  
|**DB2**|目的地是一個 IBM DB2 資料庫。|  
|**SYBASE**|目的地是一個 Sybase 資料庫。|  
  
 您必須指定這個參數。  
  
 [ **@destination_version**=] **'**_destination_version_**'**  
 這是目的地 DBMS 的產品版本。 *destination_version*已**varchar(10)**，預設值是 NULL。  
  
 [ **@destination_type**=] **'**_destination_type_**'** 輸出  
 這是目的地 DBMS 中列出的資料類型。 *destination_type*已**sysname**，預設值是 NULL。  
  
 [  **@destination_length=** ] *destination_length*輸出  
 這是目的地 DBMS 的資料類型長度。 *destination_length*已**bigint**，預設值是 NULL。  
  
 [  **@destination_precision=** ] *destination_precision*輸出  
 這是目的地 DBMS 之資料類型的有效位數。 *destination_precision*已**bigint**，預設值是 NULL。  
  
 [  **@destination_scale=** ] _destination_scale_**輸出**  
 這是目的地 DBMS 之資料類型的小數位數。 *destination_scale*已**int**，預設值是 NULL。  
  
 [  **@destination_nullable=** ] _destination_nullable_**輸出**  
 這是指目的地 DBMS 中的資料類型是否支援 NULL 值。 *destination_nullable*已**元**，預設值是 NULL。 **1**表示支援 NULL 值。  
  
 [  **@dataloss=** ]_的資料遺失_**輸出**  
 這是指對應是否可能遺失資料。 *資料遺失*已**元**，預設值是 NULL。 **1**表示會有資料遺失的可能性。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_getdefaultdatatypemapping**用於所有類型之間的複寫[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]與非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]DBMS。  
  
 **sp_getdefaultdatatypemapping**傳回的預設目的地資料類型，它是最符合指定的來源資料類型。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色可以執行**sp_getdefaultdatatypemapping**。  
  
## <a name="see-also"></a>另請參閱  
 [sp_helpdatatypemap &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)   
 [sp_setdefaultdatatypemapping &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)   
 [Oracle 訂閱者](../../relational-databases/replication/non-sql/oracle-subscribers.md)  
  
  
