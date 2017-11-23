---
title: "sp_helpdevice (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 06/10/2016
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
- sp_helpdevice
- sp_helpdevice_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_helpdevice
ms.assetid: 1a5eafa7-384e-4691-ba05-978eb73bbefb
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2a43493f69dd513b13d084cace20984cef854fb9
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="sphelpdevice-transact-sql"></a>sp_helpdevice (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  報告 Microsoft® SQL Server™ 備份裝置的相關資訊。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]我們建議您改用[sys.backup_devices](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md)目錄檢視  
  
||  
|-|  
|**適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。|  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helpdevice [ [ @devname = ] 'name' ]  
```  
  
## <a name="arguments"></a>引數  
 [  **@devname =** ] **'***名稱***'**  
 這是報告的資訊所屬的備份裝置名稱。 值*名稱*一律**sysname**。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**device_name**|**sysname**|邏輯裝置名稱。|  
|**physical_name**|**nvarchar （260)**|實體檔案名稱。|  
|**描述**|**nvarchar(255)**|裝置的描述。|  
|**status**|**int**|對應至狀態描述的數字**描述**資料行。|  
|**cntrltype**|**smallint**|裝置的控制器類型：<br /><br /> 2 = 磁碟裝置<br /><br /> 5 = 磁帶裝置|  
|**大小**|**int**|裝置大小 (2KB) 頁面。|  
  
## <a name="remarks"></a>備註  
 如果*名稱*指定，則**sp_helpdevice**顯示指定傾印裝置的相關資訊。 如果*名稱*未指定， **sp_helpdevice**顯示中的所有傾印裝置的相關資訊**sys.backup_devices**目錄檢視。  
  
 傾印裝置時，會新增至系統上，使用**sp_addumpdevice**。  
  
## <a name="permissions"></a>Permissions  
 需要 **public** 角色的成員資格。  
  
## <a name="examples"></a>範例  
 下列範例會報告 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體所有傾印裝置的相關資訊。  
  
```  
EXEC sp_helpdevice;  
```  
  
## <a name="see-also"></a>請參閱＜  
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_dropdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)   
 [Database Engine 預存程序 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
