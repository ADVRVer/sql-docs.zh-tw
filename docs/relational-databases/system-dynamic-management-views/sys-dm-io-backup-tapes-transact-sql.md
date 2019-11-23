---
title: sys.databases dm_io_backup_tapes （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_io_backup_tapes
- dm_io_backup_tapes_TSQL
- sys.dm_io_backup_tapes_TSQL
- dm_io_backup_tapes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_io_backup_tapes dynamic management view
ms.assetid: 2e27489e-cf69-4a89-9036-77723ac3de66
author: stevestein
ms.author: sstein
ms.openlocfilehash: 98902f096bb960436d764416e2563af5056f00dd
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874156"
---
# <a name="sysdm_io_backup_tapes-transact-sql"></a>sys.dm_io_backup_tapes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回磁帶裝置的清單和掛載要求的狀態，作為備份。   
 
|資料行名稱|[名稱]|描述|  
|-----------------|---------------|-----------------|  
|**physical_device_name**|**Nvarchar （520）**|可以從中取出備份的實際實體裝置名稱。 不可為 Null。|  
|**logical_device_name**|**nvarchar(256)**|使用者指定的磁片磁碟機名稱（從**sys. backup_devices**）。 如果沒有使用者指定名稱可用，便是 NULL。 可為 Null。|  
|**status**|**int**|磁帶的狀態：<br /><br /> 1 = 已開啟，可供使用<br /><br /> 2 = 掛載暫止<br /><br /> 3 = 使用中<br /><br /> 4 = 載入中<br /><br /> **注意：** 載入磁帶（**狀態 = 4**）時，媒體標籤尚未讀取。 複製媒體標籤值的資料行（例如**media_sequence_number**）會顯示預期的值，這可能會與磁帶上的實際值不同。 讀取標籤之後，[**狀態**] 會變更為**3** （使用中），而 [媒體標籤] 欄則會反映實際載入的磁帶。<br /><br /> 不可為 Null。|  
|**status_desc**|**Nvarchar （520）**|磁帶狀態的描述：<br /><br /> AVAILABLE<br /><br /> MOUNT PENDING<br /><br /> IN USE<br /><br /> LOADING MEDIA<br /><br /> 不可為 Null。|  
|**mount_request_time**|**datetime**|要求掛載的時間。 如果沒有暫止的掛接（**狀態！ = 2**），則為 Null。 可為 Null。|  
|**mount_expiration_time**|**datetime**|掛載要求將到期 (逾時) 的時間。 如果沒有暫止的掛接（**狀態！ = 2**），則為 Null。 可為 Null。|  
|**database_name**|**nvarchar(256)**|將備份至這個裝置中的資料庫。 可為 Null。|  
|**spid**|**int**|工作階段識別碼。 這用來識別磁帶的使用者。 可為 Null。|  
|命令|**int**|執行備份的命令。 可為 Null。|  
|**command_desc**|**nvarchar(120)**|命令的描述。 可為 Null。|  
|**media_family_id**|**int**|媒體家族的索引（1 ...*n*）， *n*是媒體集中的媒體家族數目。 可為 Null。|  
|**media_set_name**|**nvarchar(256)**|媒體集的名稱 (如果有的話)，依照建立媒體集時，MEDIANAME 選項中的指定。 可為 Null。|  
|**media_set_guid**|**ssNoversion**|用來唯一識別媒體集的識別碼。 可為 Null。|  
|**media_sequence_number**|**int**|媒體家族內的磁片區索引（1 ...*n*）。 可為 Null。|  
|**tape_operation**|**int**|正在執行的磁帶操作：<br /><br /> 1 = 讀取<br /><br /> 2 = 格式化<br /><br /> 3 = 初始化<br /><br /> 4 = 附加<br /><br /> 可為 Null。|  
|**tape_operation_desc**|**nvarchar(120)**|要執行的磁帶作業：<br /><br /> READ<br /><br /> FORMAT<br /><br /> INIT<br /><br /> APPEND<br /><br /> 可為 Null。|  
|**mount_request_type**|**int**|掛載要求的類型：<br /><br /> 1 = 特定磁帶。 [ **Media_\*** ] 欄位所識別的磁帶是必要的。<br /><br /> 2 = 下一個媒體家族。 要求下一個尚未還原的媒體家族。 當還原的來源裝置比媒體家族少時，便使用這個項目。<br /><br /> 3 = 接續磁帶。 將延伸媒體家族，並要求接續磁帶。<br /><br /> 可為 Null。|  
|**mount_request_type_desc**|**nvarchar(120)**|掛載要求的類型：<br /><br /> SPECIFIC TAPE<br /><br /> NEXT MEDIA FAMILY<br /><br /> CONTINUATION VOLUME<br /><br /> 可為 Null。|  
  
## <a name="permissions"></a>Permissions  
 使用者必須有這部伺服器的 VIEW SERVER STATE 權限。  
  
## <a name="see-also"></a>另請參閱  
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [I/o 相關的動態管理檢視和函數&#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  

