---
description: sp_helpreplicationoption (Transact-SQL)
title: sp_helpreplicationoption (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpreplicationoption
- sp_helpreplicationoption_TSQL
helpviewer_keywords:
- sp_helpreplicationoption
ms.assetid: ef988dbc-dd0b-4132-80ab-81eebec1cffe
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 80d34e406b7672e31dd9cb70f42431bcd7392917
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464202"
---
# <a name="sp_helpreplicationoption-transact-sql"></a>sp_helpreplicationoption (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  顯示伺服器所啟用的複寫選項類型。 這個預存程序執行於任何資料庫的任何伺服器。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helpreplicationoption [ [ @optname =] 'option_name' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @optname = ] 'option_name'` 這是要查詢的複寫選項名稱。 *option_name* 是 **sysname**，預設值是 Null。  
  
|值|描述|  
|-----------|-----------------|  
|**事務**|如果是啟用異動複寫，則傳回結果集。|  
|**合併**|如果是啟用合併式複寫，則傳回結果集。|  
|NULL (預設值)|不會傳回結果集。|  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**optname**|**sysname**|複寫選項的名稱，它可以是下列值之一：<br /><br /> **事務**<br /><br /> **合併**|  
|**value**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**major_version**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**minor_version**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**修訂**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**install_failures**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或 **1** (失敗)   
  
## <a name="remarks"></a>備註  
 **sp_helpreplicationoption** 用來取得特定伺服器上啟用之複寫選項的相關資訊。 若要取得特定資料庫的資訊，請使用 **sp_helpreplicationdboption**。  
  
## <a name="permissions"></a>權限  
 執行許可權預設為 **public** 角色。  
  
## <a name="see-also"></a>另請參閱  
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
