---
description: sp_dropextendedproc (Transact-SQL)
title: sp_dropextendedproc (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 10/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropextendedproc
- sp_dropextendedproc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropextendedproc
ms.assetid: dd93af2c-1b7d-4e39-af23-2d21d270a381
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0bf9c7d760b059c5608d4af1c13a7758aaa428c3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447223"
---
# <a name="sp_dropextendedproc-transact-sql"></a>sp_dropextendedproc (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  卸除擴充預存程序。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 請改用 [CLR 整合](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) 。  
  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
sp_dropextendedproc [ @functname = ] 'procedure'   
```  
  
## <a name="arguments"></a>引數  
`[ @functname = ] 'procedure'` 這是要卸載的擴充預存程式名稱。 程式是**Nvarchar (517) ** *，沒有預設*值。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="remarks"></a>備註  
 執行 **sp_dropextendedproc** 會從 [sys.databases](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) 目錄檢視卸載使用者定義的擴充預存程式名稱，並從 [sys. extended_procedures](../../relational-databases/system-catalog-views/sys-extended-procedures-transact-sql.md) 目錄檢視中移除專案。 這個預存程式只能在 **master** 資料庫中執行。  
  
**sp_dropextendedproc** 不會卸載系統擴充預存程式。 相反地，系統管理員應該拒絕將擴充預存程式的 EXECUTE 許可權授與 **public** 角色。  
  
 **sp_dropextendedproc** 無法在交易內執行。  
  
## <a name="permissions"></a>權限  
 只有 **系統管理員（sysadmin** ）固定伺服器角色的成員，才可以執行 **sp_dropextendedproc**。  
  
## <a name="examples"></a>範例  
 下列範例會卸除 `xp_hello` 擴充預存程序。  
  
> [!NOTE]  
>  這個擴充預存程序必須已經存在，否則該範例會傳回錯誤訊息。  
  
```  
USE master;  
GO  
EXEC sp_dropextendedproc 'xp_hello';  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_addextendedproc &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_helpextendedproc &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
