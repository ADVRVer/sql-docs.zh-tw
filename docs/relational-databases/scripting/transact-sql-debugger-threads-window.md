---
title: "執行緒視窗 | Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.threads
helpviewer_keywords:
- Threads Window [Transact-SQL]
ms.assetid: e153f619-0049-4162-9076-c24a454f3278
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 50d5602a6bf16946b95e7baae0ffcc4181e38eca
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2018
---
# <a name="transact-sql-debugger---threads-window"></a>Transact-SQL 偵錯工具 - 執行緒視窗
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] [執行緒] 視窗會顯示有關所偵錯之[!INCLUDE[ssDE](../../includes/ssde-md.md)]查詢編輯器工作階段使用的[!INCLUDE[ssDE](../../includes/ssde-md.md)]執行緒資訊。 您必須在偵錯模式中，才能顯示執行緒資訊。  
  
## <a name="task-list"></a>工作清單  
 **若要存取執行緒視窗**  
  
-   在 [偵錯] 功能表中，按一下 [視窗]，再按一下 [執行緒]。  
  
## <a name="columns"></a>[資料行]  
 **ID**  
 這是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具指派給執行緒的唯一識別碼。 您可以從 sys.dm_os_threads 動態管理檢視選取資料列，以尋找有關執行緒的詳細資訊。  
  
 如果您不是在輕量型共用模式下執行，請選取一個資料列，其中的 os_thread_id 值符合 [識別碼] 資料行中的值。 如果您在輕量型共用模式下執行，請選取一個資料列，其中的 fiber_context_address 值符合 [識別碼] 資料行中的值。  
  
 **名稱**  
 使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ComputerName/InstanceName [SPID] **格式顯示有關**工作階段的資訊。  
  
 **ComputerName**  
 正在執行查詢編輯器工作階段連接之 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體的電腦名稱。  
  
 **InstanceName**  
 查詢編輯器工作階段連接之 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體的名稱。  
  
 **[SPID]**  
 可唯一識別此工作階段的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工作階段處理序識別碼。 您可以取得有關此工作階段的資訊，其方式是在 sys.sysprocesses 檢視表中選取與 spid 資料行有相同值的資料列。  
  
 **位置**  
 顯示所偵錯之查詢編輯器工作階段內使用的指令碼檔案名稱。  
  
 **優先權**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具不支援這個功能。  
  
 **暫止**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具不支援這個功能。  
  
## <a name="see-also"></a>另請參閱  
 [Transact-SQL 偵錯工具](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Transact-SQL 偵錯工具資訊](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [sys.dm_os_threads &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql.md)   
 [sys.sysprocesses &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)  
  
  
