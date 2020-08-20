---
description: sp_changereplicationserverpasswords (Transact-SQL)
title: sp_changereplicationserverpasswords (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changereplicationserverpasswords_TSQL
- sp_changereplicationserverpasswords
helpviewer_keywords:
- sp_changereplicationserverpasswords
ms.assetid: 9333da96-3a1c-4adb-9a74-5dac9ce596df
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0d0e07afbf3837768ac2b57e3dfaa7d0c8c0d0af
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481464"
---
# <a name="sp_changereplicationserverpasswords-transact-sql"></a>sp_changereplicationserverpasswords (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  變更在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連接到複寫拓撲中的伺服器時，複寫代理程式所使用之 Windows 帳戶或登入的已儲存密碼。 通常您必須變更在伺服器執行的每個個別代理程式的密碼，即使它們都使用相同的登入或帳戶也不例外。 這個預存程序可讓您變更所有在伺服器執行的複寫代理程式所用的給定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入或 Windows 帳戶之所有執行個體的密碼。 這個預存程序執行於 master 資料庫複寫拓撲中的任何一部伺服器。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_changereplicationserverpasswords [ @login_type = ] login_type  
        , [ @login = ] 'login'   
        , [ @password = ] 'password'  
    [ , [ @server = ] 'server' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @login_type = ] login_type` 這是所提供之認證的驗證類型。 *login_type* 是 **Tinyint**，沒有預設值。  
  
 **1** = Windows 整合式驗證  
  
 **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證  
  
`[ @login = ] 'login'` 這是要變更的 Windows 帳戶或登入的名稱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 *登* 入是 **Nvarchar (257) **，沒有預設值  
  
`[ @password = ] 'password'` 這是要為指定的 *登*入儲存的新密碼。 *password* 是 **sysname**，沒有預設值。  
  
> [!NOTE]  
>  在變更複寫密碼之後，必須停止並重新啟動使用該代理程式變更生效前所用密碼的每一個代理程式。  
  
`[ @server = ] 'server'` 這是要變更儲存密碼的伺服器連接。 *伺服器* 是 **sysname**，它可以是下列其中一個值：  
  
|值|描述|  
|-----------|-----------------|  
|**轉銷商**|所有與散發者的代理程式連接。|  
|**publisher**|所有與發行者的代理程式連接。|  
|**使用者**|所有與訂閱者的代理程式連接。|  
|**%** (預設) |所有與複寫拓撲中所有伺服器的代理程式連接。|  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或 **1** (失敗)   
  
## <a name="remarks"></a>備註  
 **sp_changereplicationserverpasswords** 用於所有類型的複寫。  
  
## <a name="permissions"></a>權限  
 只有 **系統管理員（sysadmin** ）固定伺服器角色的成員，才可以執行 **sp_changereplicationserverpasswords**。  
  
## <a name="see-also"></a>另請參閱  
 [檢視及修改複寫安全性設定](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
  
