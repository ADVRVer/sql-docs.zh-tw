---
title: sp_helpdevice （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpdevice
- sp_helpdevice_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdevice
ms.assetid: 1a5eafa7-384e-4691-ba05-978eb73bbefb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 59b7f4a0cf0c3ba3335a181b35560af8847fca8b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824510"
---
# <a name="sp_helpdevice-transact-sql"></a>sp_helpdevice (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  報告 Microsoft® SQL Server™ 備份裝置的相關資訊。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]我們建議您改用[sys.databases backup_devices](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md)目錄檢視  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helpdevice [ [ @devname = ] 'name' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @devname = ] 'name'`這是要報告其資訊的備份裝置名稱。 *Name*的值一律為**sysname**。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**device_name**|**sysname**|邏輯裝置名稱。|  
|**physical_name**|**nvarchar(260)**|實體檔案名稱。|  
|**描述**|**nvarchar(255)**|裝置的描述。|  
|**status**|**int**|對應至 [**描述**] 資料行中狀態原因的數位。|  
|**cntrltype**|**smallint**|裝置的控制器類型：<br /><br /> 2 = 磁碟裝置<br /><br /> 5 = 磁帶裝置|  
|**size**|**int**|裝置大小 (2KB) 頁面。|  
  
## <a name="remarks"></a>備註  
 如果指定了*name* ， **sp_helpdevice**會顯示指定傾印裝置的相關資訊。 如果未指定*name* ， **sp_helpdevice**會顯示**sys.databases backup_devices**目錄檢視中所有傾印裝置的相關資訊。  
  
 傾印裝置會使用**sp_addumpdevice**新增至系統。  
  
## <a name="permissions"></a>權限  
 需要 **public** 角色的成員資格。  
  
## <a name="examples"></a>範例  
 下列範例會報告 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體所有傾印裝置的相關資訊。  
  
```  
EXEC sp_helpdevice;  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_dropdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)   
 [資料庫引擎預存程式 &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
