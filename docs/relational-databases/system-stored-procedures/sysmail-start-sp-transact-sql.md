---
title: "sysmail_start_sp (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_start_sp
- sysmail_start_sp_TSQL
dev_langs: TSQL
helpviewer_keywords: sysmail_start_sp
ms.assetid: 25fd7bb6-cfdd-463f-bea8-c6fcb805d3f5
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: abfda7b6f83e30a0d19706fc2182b9f2352435c9
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2017
---
# <a name="sysmailstartsp-transact-sql"></a>sysmail_start_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  啟動外部程式使用的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 物件來啟動 Database Mail。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sysmail_start_sp  
```  
  
## <a name="arguments"></a>引數  
 無  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 無  
  
## <a name="remarks"></a>備註  
 Database Mail 未啟用或安裝[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]安裝。 請使用 Database Mail 組態精靈來啟用和安裝 Database Mail 物件。  
  
 這個預存程序處於**msdb**資料庫。 這個預存程序會啟動存放外送訊息要求的 Database Mail 佇列，而且會啟用外部程式的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 啟動作業。  
  
 當啟動佇列時，Database Mail 外部程式可以處理訊息。 此程序可讓您停止佇列之後，重新啟動佇列**sysmail_stop_sp**預存程序。  
  
> [!NOTE]  
>  這個預存程序只會啟動 Database Mail 的佇列。 這個預存程序不會啟動資料庫中的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 訊息傳遞。  
  
## <a name="permissions"></a>Permissions  
 執行此程序預設值，成員的權限**sysadmin**固定的伺服器角色。  
  
## <a name="examples"></a>範例  
 下列範例示範中啟動 Database Mail **msdb**資料庫。 這個範例假設您已啟用 Database Mail。  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_start_sp ;  
GO  
```  
  
## <a name="see-also"></a>請參閱  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail Xp 伺服器組態選項](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md)   
 [sysmail_stop_sp &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql.md)   
 [Database Mail 預存程序 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
