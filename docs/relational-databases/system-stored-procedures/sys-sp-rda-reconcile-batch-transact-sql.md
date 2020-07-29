---
title: sys.databases sp_rda_reconcile_batch （Transact-sql） |Microsoft Docs
description: 瞭解如何使用 sp_rda_reconcile_batch sys.databases 來協調已啟用 Stretch 之 SQL Server 資料表中的批次識別碼，以及儲存在遠端 Azure 資料表中的批次識別碼。
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_batch
- sys.sp_rda_reconcile_batch_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_batch stored procedure
ms.assetid: 6d21eac3-7b6c-4fe0-8bc4-bf503f3948a6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: aa97030851e13eac020564eec7931a00595b8884
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247087"
---
# <a name="syssp_rda_reconcile_batch-transact-sql"></a>sys.databases sp_rda_reconcile_batch （Transact-sql）
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  將儲存在已啟用延展功能之 SQL Server 資料表中的批次識別碼，與儲存在遠端 Azure 資料表中的批次識別碼協調。  
  
 通常只有在您已手動刪除遠端資料表中最近遷移的資料時，才需要執行**sp_rda_reconcile_batch** 。 當您手動刪除包含最新批次的遠端資料時，批次識別碼不會同步處理，而且會停止遷移。  
 
 若要刪除已遷移至 Azure 的資料，請參閱此頁面上的備註。
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>語法  
  
```  
  
sp_rda_reconcile_batch @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>引數  
 \@objname = '* \@ objname*'  
 已啟用延展功能之 SQL Server 資料表的名稱。  
  
## <a name="permissions"></a>權限  
 需要 db_owner 許可權。  
  
## <a name="remarks"></a>備註  
 如果您想要刪除已遷移至 Azure 的資料，請執行下列動作。  
  
1.  暫停資料移轉。 如需詳細資訊，請參閱[暫停和繼續資料移轉 &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md)。  
  
2.  藉由使用 STAGE_ONLY 提示來執行 DELETE 命令，以刪除 SQL Server 臨時表中的資料。 如需詳細資訊，請參閱[進行系統管理更新和刪除](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md#adminHints)。
  
3.  藉由使用 REMOTE_ONLY 提示來執行 DELETE 命令，以從遠端 Azure 資料表中刪除相同的資料。  
  
4.  執行**sp_rda_reconcile_batch**。  
  
5.  繼續資料移轉。 如需詳細資訊，請參閱[暫停和繼續資料移轉 &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md)。  
  
## <a name="example"></a>範例  
 若要協調批次識別碼，請執行下列語句。  
  
```sql  
EXEC sp_rda_reconcile_batch @objname = N'StretchEnabledTableName';  
```  
  
  
