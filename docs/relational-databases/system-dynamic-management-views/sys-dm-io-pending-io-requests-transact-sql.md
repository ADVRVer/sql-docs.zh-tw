---
title: sys.databases dm_io_pending_io_requests （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_io_pending_io_requests
- dm_io_pending_io_requests
- dm_io_pending_io_requests_TSQL
- sys.dm_io_pending_io_requests_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_io_pending_io_requests dynamic management view
ms.assetid: d1fb46dd-5c74-4c04-9ecf-8934b1bedb5b
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 84bbf050161e6b66d10a1e7ce858459736248847
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827897"
---
# <a name="sysdm_io_pending_io_requests-transact-sql"></a>sys.dm_io_pending_io_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中每一項暫止 I/O 要求，各傳回一個資料列。  
  
> [!NOTE]  
>  若要從或呼叫此 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] ，請使用**dm_pdw_nodes_io_pending_io_requests**的名稱。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**io_completion_request_address**|**varbinary(8)**|IO 要求的記憶體位址。 不可為 Null。|  
|**io_type**|**nvarchar(60)**|暫止 I/O 要求的類型。 不可為 Null。|  
|**io_pending_ms_ticks**|**bigint**|僅供內部使用。 不可為 Null。| 
|**io_pending**|**int**|指出 I/O 要求是否暫止，或已由 Windows 完成。 I/O 要求仍然暫止，即使 Windows 已完成該要求，但 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 尚未執行內容切換，來處理 I/O 要求及從這份清單中移除它。 不可為 Null。|  
|**io_completion_routine_address**|**varbinary(8)**|完成 I/O 要求時要呼叫的內部函數。 可為 Null。|  
|**io_user_data_address**|**varbinary(8)**|僅供內部使用。 可為 Null。|  
|**scheduler_address**|**varbinary(8)**|發出這項 I/O 要求所在的排程器。 I/O 要求將出現在排程器的暫止 I/O 清單上。 如需詳細資訊，請參閱[dm_os_schedulers &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md)。 不可為 Null。|  
|**io_handle**|**varbinary(8)**|用於 I/O 要求之檔案的檔案控制代碼。 可為 Null。|  
|**io_offset**|**bigint**|I/O 要求的位移。 不可為 Null。|  
|**io_handle_path**|**nvarchar(256)**| I/o 要求中所使用的檔案路徑。 可為 Null。|
|**pdw_node_id**|**int**|**適用**于： [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此散發所在節點的識別碼。|  
  
## <a name="permissions"></a>權限  

在上 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ，需要 `VIEW SERVER STATE` 許可權。   
在高階 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 層級上，需要 `VIEW DATABASE STATE` 資料庫的許可權。 在 [ [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 標準] 和 [基本] 層上，需要**伺服器管理員**或**Azure Active Directory 系統管理員**帳戶。   
  
## <a name="see-also"></a>另請參閱  
 [動態管理 Views 和函數 &#40;Transact-sql&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [I/o 相關的動態管理檢視和函數 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


