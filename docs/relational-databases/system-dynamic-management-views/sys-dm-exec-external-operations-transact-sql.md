---
description: 'sys. dm_exec_external_operations (Transact-sql) '
title: sys. dm_exec_external_operations (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_EXTERNAL_OPERATIONS_TSQL
- DM_EXEC_EXTERNAL_OPERATIONS
- SYS.DM_EXEC_EXTERNAL_OPERATIONS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- sys.dm_exec_external_operations management view
- dm_exec_external_operations management view
ms.assetid: d268217a-85b8-4b7f-9cd1-87865eba2be1
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cfb27c27e680e253cbafc0d30a4e4db0cd6d9ed4
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89548530"
---
# <a name="sysdm_exec_external_operations-transact-sql"></a>sys. dm_exec_external_operations (Transact-sql) 
[!INCLUDE [sqlserver2016-asa-pdw](../../includes/applies-to-version/sqlserver2016-asa-pdw.md)]

  捕捉外部 PolyBase 作業的相關資訊。  
  
|資料行名稱|資料類型|描述|範圍|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|與 PolyBase 查詢相關聯的唯一查詢識別碼|請參閱[sys. dm_exec_requests 中 &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)的識別碼|  
|step_index|**int**|查詢步驟的索引|請參閱[sys. dm_exec_distributed_request_steps &#40;transact-sql](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md)中的 step_index&#41;|  
|operation_ 類型|**nvarchar(128)**|描述 Hadoop 操作或其他外部操作|「外部 Hadoop 作業」|  
|operation_ 名稱|**nvarchar(4000)**|指出工作的狀態（以百分比為單位） (所耗用的輸入量) |0-1-乘以因數 100 (完成) |  
|map_ 進度|**float**|指出縮減工作的狀態（如果有的話）|0-1-乘以因數 100 (完成) |  
  
## <a name="see-also"></a>另請參閱  
 [使用動態管理檢視進行 PolyBase 疑難排解](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [資料庫相關的動態管理檢視 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
