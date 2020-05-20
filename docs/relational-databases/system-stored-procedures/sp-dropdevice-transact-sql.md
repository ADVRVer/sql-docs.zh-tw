---
title: sp_dropdevice （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropdevice_TSQL
- sp_dropdevice
dev_langs:
- TSQL
helpviewer_keywords:
- backup devices [SQL Server], deleting
- sp_dropdevice
ms.assetid: c8b07189-7c35-414b-acc1-45bd6e7e17c3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8d9176624f661cb012fe8ed3124a1b868ec72195
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830192"
---
# <a name="sp_dropdevice-transact-sql"></a>sp_dropdevice (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  從的實例卸載資料庫裝置或備份裝置 [!INCLUDE[ssDEversion2005](../../includes/ssdeversion2005-md.md)] ，並從**sysdevices**中刪除專案。  
   
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_dropdevice [ @logicalname = ] 'device'   
    [ , [ @delfile = ] 'delfile' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @logicalname = ] 'device'`這是**master.dbo.sysdevices.name**中所列的資料庫裝置或備份裝置的邏輯名稱。 *裝置*為**sysname**，沒有預設值。  
  
`[ @delfile = ] 'delfile'`指定是否應該刪除實體備份裝置檔案。 *delfile*是**Varchar （7）**。 如果指定為**DELFILE**，則會刪除實體備份裝置磁片檔案。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="remarks"></a>備註  
 **sp_dropdevice**不能用在交易內部。  
  
## <a name="permissions"></a>權限  
 需要 **diskadmin** 固定伺服器角色的成員資格。  
  
## <a name="examples"></a>範例  
 下列範例會從 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中卸除 `tapedump1` 磁帶傾印裝置。  
  
```  
EXEC sp_dropdevice 'tapedump1';  
```  
  
## <a name="see-also"></a>另請參閱  
 [備份裝置 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [刪除備份裝置 &#40;SQL Server&#41;](../../relational-databases/backup-restore/delete-a-backup-device-sql-server.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_helpdb &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helpdevice &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpdevice-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
