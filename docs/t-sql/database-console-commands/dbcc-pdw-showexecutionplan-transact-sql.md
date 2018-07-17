---
title: DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/16/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.suite: sql
ms.component: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: uc-msft
ms.author: umajay
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 83826259d76cbe27cad4451baed07221e6afed2c
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36895881"
---
# <a name="dbcc-pdwshowexecutionplan-transact-sql"></a>DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

顯示在特定的 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 或 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] 計算節點或控制節點上執行之查詢的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行計劃。 在計算節點或控制節點上執行查詢時，此命令可用來對查詢效能問題進行疑難排解。
  
一旦了解計算節點上執行之 SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查詢的查詢效能問題，有許多方法可以改善。 可改善計算節點上之查詢效能的可能方法包括建立多重資料行統計資料、建立非叢集索引或使用查詢提示。
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>語法  
SQL Server 的語法：

```sql
DBCC PDW_SHOWEXECUTIONPLAN ( distribution_id, spid )  
[;]  
```  
Azure 平行處理資料倉儲的語法：
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( pdw_node_id, spid )  
[;]  
```  
  
## <a name="arguments"></a>引數  
 *distribution_id*  
 執行查詢計劃之分佈的識別碼。 此為整數，而且不得為 NULL。 以 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 為目標時使用。  
  
 *pdw_node_id*  
 執行查詢計劃之節點的識別碼。 此為整數，而且不得為 NULL。 以設備為目標時使用。  
  
 *spid*  
 執行查詢計劃之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工作階段的識別碼。 此為整數，而且不得為 NULL。  
  
## <a name="permissions"></a>Permissions  
 需要 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 的 CONTROL 權限。  
  
需要設備的 VIEW-SERVER-STATE 權限。
  
## <a name="examples-includesssdwincludessssdw-mdmd"></a>範例：[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]  
  
### <a name="a-dbcc-pdwshowexecutionplan-basic-syntax"></a>A. DBCC PDW_SHOWEXECUTIONPLAN 基本語法  
 在 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 執行個體上執行時，請修改上述查詢以同時選取 distribution_id。  
  
```sql
SELECT [sql_spid], [pdw_node_id], [request_id], [dms_step_index], [type], [start_time], [end_time], [status], [distribution_id]  
FROM sys.dm_pdw_dms_workers   
WHERE [status] <> 'StepComplete' and [status] <> 'StepError'  
order by request_id, [dms_step_index];  
```  
  
這會傳回每個主動執行之分佈的 spid。 如果您對工作階段 375 中執行何種分佈 1 感興趣，建議您執行下列命令。
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( 1, 375 );  
```  

## <a name="examples-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="b-dbcc-pdwshowexecutionplan-basic-syntax"></a>B. DBCC PDW_SHOWEXECUTIONPLAN 基本語法  
 執行太久的查詢是執行 DMS 查詢計劃作業或 SQL 查詢計劃作業的查詢。  
  
如果查詢執行的是 DMS 查詢計劃作業，您可以使用下列查詢來擷取未完成之步驟的節點識別碼和工作階段識別碼清單。
  
```sql
SELECT [sql_spid], [pdw_node_id], [request_id], [dms_step_index], [type], [start_time], [end_time], [status]   
FROM sys.dm_pdw_dms_workers   
WHERE [status] <> 'StepComplete' and [status] <> 'StepError'  
AND pdw_node_id = 201001   
order by request_id, [dms_step_index], [distribution_id];  
```  
  
根據先前查詢的結果，使用 sql_spid 和 pdw_node_id 做為 DBCC PDW_SHOWEXEUCTIONPLAN 的參數。 例如，下列命令會顯示 pdw_node_id 201001 和 sql_spid 375 的執行計劃。
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( 201001, 375 );  
```  

## <a name="see-also"></a>另請參閱
[DBCC PDW_SHOWPARTITIONSTATS &#40;Transact-SQL&#41;](dbcc-pdw-showpartitionstats-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED &#40;Transact-SQL&#41;](dbcc-pdw-showspaceused-transact-sql.md)
