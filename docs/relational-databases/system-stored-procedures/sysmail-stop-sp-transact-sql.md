---
title: sysmail_stop_sp （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_stop_sp_TSQL
- sysmail_stop_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_stop_sp
ms.assetid: 045ee36f-5bf0-4626-b5ee-e84db06ce16f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c6ed9d4a05759495090a35224e5aa5ef805e520f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85783703"
---
# <a name="sysmail_stop_sp-transact-sql"></a>sysmail_stop_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  停止外部程式使用的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 物件來停止 Database Mail。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sysmail_stop_sp  
```  
  
## <a name="arguments"></a>引數  
 None  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功）或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 這個預存程式是在**msdb**資料庫中。  
  
 這個預存程序會停止存放外送訊息要求的 Database Mail 佇列，而且會關閉外部程式的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 啟用作業。  
  
 當佇列停止時，Database Mail 外部程式不會處理訊息。 這個預存程序可讓您停止 Database Mail 來進行疑難排解或維護。  
  
 若要開始 Database Mail，請使用**sysmail_start_sp**。 請注意，當物件停止時， **sp_send_dbmail**仍接受 mail [!INCLUDE[ssSB](../../includes/sssb-md.md)] 。  
  
> [!NOTE]  
>  這個預存程序只會停止 Database Mail 的佇列。 這個預存程序不會停用資料庫中的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 訊息傳遞。 這個預存程序不會停用 Database Mail 擴充預存程序來縮減介面區域。 若要停用擴充預存程式，請參閱**sp_configure**系統預存程式的[Database Mail xp 選項](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md)。  
  
## <a name="permissions"></a>權限  
 此程式的執行許可權預設為**系統管理員（sysadmin** ）固定伺服器角色的成員。  
  
## <a name="examples"></a>範例  
 下列範例會顯示如何停止**msdb**資料庫中的 Database Mail。 這個範例假設您已啟用 Database Mail。  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_stop_sp ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [sysmail_start_sp &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql.md)   
 [Database Mail 預存程式 &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
