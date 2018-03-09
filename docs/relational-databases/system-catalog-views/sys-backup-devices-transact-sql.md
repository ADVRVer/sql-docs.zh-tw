---
title: "只有當 sys.backup_devices (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- backup_devices_TSQL
- backup_devices
- sys.backup_devices
- sys.backup_devices_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup devices [SQL Server], viewing information
- sys.backup_devices catalog view
ms.assetid: 457edaa4-aca1-4bd3-bf8d-734490b80fcd
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8c3e73f8ed9f7d19f52d40742ea029d664b02ea8
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a name="sysbackupdevices-transact-sql"></a>sys.backup_devices (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  包含使用註冊每個備份裝置的資料列**sp_addumpdevice**或已建立在[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|備份裝置的名稱。 在整組中，這是唯一的。|  
|**type**|**tinyint**|備份裝置的類型：<br /><br /> 2 = 磁碟<br /><br /> 3 = 磁片 (已棄用)<br /><br /> 5 = 磁帶<br /><br /> 6 = 管道 (已棄用)<br /><br /> 7 = 虛擬裝置 (供協力廠商備份供應商選擇性使用)<br /><br /> 通常只用磁碟 (2) 和磁帶 (5)。|  
|**type_desc**|**nvarchar(60)**|備份裝置類型的描述：<br /><br /> DISK<br /><br /> DISKETTE (已棄用)<br /><br /> TAPE<br /><br /> PIPE (已棄用)<br /><br /> VIRTUAL_DEVICE (供協力廠商備份供應商選擇性使用)<br /><br /> 通常只用 DISK 和 TAPE。|  
|**physical_name**|**nvarchar(260)**|備份裝置的實體檔案名稱或路徑。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [備份裝置 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [資料庫和檔案目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [查詢 SQL Server 系統目錄常見問題集](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
