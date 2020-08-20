---
description: sp_helpextendedproc (Transact-SQL)
title: sp_helpextendedproc (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpextendedproc
- sp_helpextendedproc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpextendedproc
ms.assetid: 7e1f017e-c898-4225-b375-6a73ef9aac7b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 68bc88bdaddc873c0f272ffef37d6465cddb45af
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493221"
---
# <a name="sp_helpextendedproc-transact-sql"></a>sp_helpextendedproc (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  報告目前定義的擴充預存程序及程序 (函數) 所屬之動態連結程式庫 (DLL) 的名稱。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 請改用 [CLR 整合](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) 。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helpextendedproc [ [@funcname = ] 'procedure' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @funcname = ] 'procedure'` 這是要報告其資訊的擴充預存程式名稱。 程式是**sysname**，預設*值是 Null* 。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|擴充預存程序的名稱。|  
|**dll**|**nvarchar(255)**|DLL 的名稱。|  
  
## <a name="remarks"></a>備註  
 當 *指定了程式* 時， **sp_helpextendedproc** 所指定擴充預存程式上的報表。 如果未提供這個參數， **sp_helpextendedproc** 會傳回所有擴充預存程式名稱，以及每個擴充預存程式所屬的 DLL 名稱。  
  
## <a name="permissions"></a>權限  
 授與執行 **sp_helpextendedproc** 的許可權授與 **public**。  
  
## <a name="examples"></a>範例  
  
### <a name="a-reporting-help-on-all-extended-stored-procedures"></a>A. 報告所有擴充預存程序的說明  
 下列範例會報告所有擴充預存程序。  
  
```  
USE master;  
GO  
EXEC sp_helpextendedproc;  
GO  
```  
  
### <a name="b-reporting-help-on-a-single-extended-stored-procedure"></a>B. 報告單一擴充預存程序的說明  
 下列範例會報告 `xp_cmdshell` 擴充預存程式。  
  
```  
USE master;  
GO  
EXEC sp_helpextendedproc xp_cmdshell;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_addextendedproc &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
