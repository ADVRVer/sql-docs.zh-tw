---
title: 刪除追蹤 (Transact-SQL) | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], deleting
- removing traces
- deleting traces
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3e7338e9068c1b8c58623cf744022a165ce90eda
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "71952716"
---
# <a name="delete-a-trace-transact-sql"></a>刪除追蹤 (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  本主題說明如何使用預存程序來刪除追蹤。  
  
 如需使用追蹤預存程序的範例，請參閱[建立追蹤 &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)。  
  
### <a name="to-delete-a-trace"></a>若要刪除追蹤  
  
1.  指定 **，執行** sp_trace_setstatus`@status = 0` 以停止追蹤。  
  
2.  指定 **，執行** sp_trace_setstatus`@status = 2` 以關閉追蹤，並將其資訊從伺服器中刪除。  
  
> [!NOTE]  
>  您必須先關閉追蹤，才能將它刪除。  
  
## <a name="see-also"></a>另請參閱  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [SQL Server Profiler 預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  
