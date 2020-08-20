---
description: sp_helpmergepartition (Transact-SQL)
title: sp_helpmergepartition (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergepartition
- sp_helpmergepartition_TSQL
helpviewer_keywords:
- sp_helpmergepartition
ms.assetid: 184188cc-f519-445d-97ce-aae38f1eb550
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e7824eb6e547b8bacec2cae297e5f236376d0aa0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474017"
---
# <a name="sp_helpmergepartition-transact-sql"></a>sp_helpmergepartition (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  傳回指定合併式發行集的資料分割資訊。 這個預存程序執行於任何資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helpmergepartition [ @publication= ] 'publication'   
    [ , [ @suser_sname = ] 'suser_sname' ]  
    [ , [ @host_name = ] 'host_name' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @publication = ] 'publication'` 這是發行集的名稱。 *發行* 集是 **sysname**，沒有預設值。  
  
`[ @suser_sname = ] 'suser_sname'` 這是用來定義資料分割的 SUSER_SNAME 值。 *suser_sname* 是 **sysname**，預設值是 Null。 請提供這個參數，將結果集限制於 SUSER_SNAME 解析成所提供的值之資料分割。  
  
> [!NOTE]  
>  當提供 *suser_sname* 時， *HOST_NAME* 必須是 Null  
  
`[ @host_name = ] 'host_name'` 這是用來定義資料分割的 HOST_NAME 值。 *host_name* 是 **sysname**，預設值是 Null。 請提供這個參數，將結果集限制於 HOST_NAME 解析成所提供的值之資料分割。  
  
> [!NOTE]  
>  當提供 *suser_sname* 時， *HOST_NAME* 必須是 Null  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**分區**|**int**|識別訂閱者資料分割。|  
|**host_name**|**sysname**|針對訂閱者的 [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) 函數值所篩選的訂閱，建立資料分割時所使用的值。|  
|**suser_sname**|**sysname**|針對訂閱者的 [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) 函數值所篩選的訂閱，建立資料分割時所使用的值。|  
|**dynamic_snapshot_location**|**nvarchar(255)**|訂閱者的資料分割之篩選資料快照集的位置。|  
|**date_refreshed**|**datetime**|上次執行快照集作業來產生資料分割的篩選資料快照集的日期。|  
|**dynamic_snapshot_jobid**|**uniqueidentifier**|識別建立資料分割之篩選資料快照集的作業。|  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或 **1** (失敗)   
  
## <a name="remarks"></a>備註  
 **sp_helpmergepartition** 用於合併式複寫中。  
  
## <a name="permissions"></a>權限  
 只有 **系統管理員（sysadmin** ）固定伺服器角色和 **db_owner** 固定資料庫角色的成員，才能夠執行 **sp_helpmergepartition**。  
  
## <a name="see-also"></a>另請參閱  
 [sp_addmergepartition &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md)   
 [sp_dropmergepartition &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql.md)  
  
  
