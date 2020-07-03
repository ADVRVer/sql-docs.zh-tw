---
title: sp_schemafilter （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_schemafilter_TSQL
- sp_schemafilter
helpviewer_keywords:
- sp_schemafilter
ms.assetid: 199e869b-2cd2-44ee-b2ee-69edb06a1bc4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 116dde1f0fd62f96e31a164ff06472de5b527938
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85901341"
---
# <a name="sp_schemafilter-transact-sql"></a>sp_schemafilter (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  修改和顯示當列出適合發行的 Oracle 資料表時所排除之結構描述的相關資訊。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_schemafilter [ @publisher = ] 'publisher'   
   [ , [ @schema = ] 'schema' ]   
   [ , [ @operation = ] 'operation' ]   
```  
  
## <a name="arguments"></a>引數  
`[ @publisher = ] 'publisher'`這是非發行者的名稱 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 *publisher*是**sysname**，沒有預設值。  
  
`[ @schema = ] 'schema'`這是架構的名稱。 *架構*是**sysname**，預設值是 Null。  
  
`[ @operation = ] 'operation'`這是要對此架構採取的動作。 *operation*是**Nvarchar （4）**，它可以是下列值之一。  
  
|值|說明|  
|-----------|-----------------|  
|**add**|將指定的結構描述加入不適合發行的結構描述清單中。|  
|**下拉式**|從不適合發行的結構描述清單中，卸除指定的結構描述。|  
|**說明**|傳回不適合發行的結構描述清單。|  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**schemaname**|**sysname**|這是不適合發行的結構描述名稱。|  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功）或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_schemafilter**只應用於異類發行者。  
  
## <a name="permissions"></a>權限  
 只有在散發者端的**系統管理員（sysadmin** ）固定伺服器角色的成員，才能夠執行**sp_schemafilter**。  
  
## <a name="see-also"></a>另請參閱  
 [複寫預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
