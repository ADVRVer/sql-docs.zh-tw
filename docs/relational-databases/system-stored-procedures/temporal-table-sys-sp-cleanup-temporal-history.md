---
title: sys.sp_cleanup_temporal_history |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6eff30b4-b261-4f1f-b93c-1f69d754298d
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 111986a771b9cfb156c0d37688565b39401411f8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68037236"
---
# <a name="sysspcleanuptemporalhistory-transact-sql"></a>sys.sp_cleanup_temporal_history & Amp;#40;transact-SQL&AMP;#41;
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

移除符合在單一交易中的設定的 HISTORY_RETENTION 時段的時態性記錄資料表中的所有資料列。
  
## <a name="syntax"></a>語法  
```  
sp_cleanup_temporal_history [@schema_name = ] schema_name, [@table_name = ] table_name [, [@row_count=] @row_count_var [OUTPUT]]
```  
  
## <a name="arguments"></a>引數  

*@table_name*

時態表的保留清除會叫用的名稱。

*schema_name*

哪些目前時態表所屬的結構描述名稱

*row_count_var* [OUTPUT]

輸出參數傳回的已刪除的資料列數目。 如果記錄資料表有叢集資料行存放區索引，這個參數會傳回永遠為 0。
  
## <a name="remarks"></a>備註
這個預存程序可用只能搭配時態表，具有有限的保留期限指定。
只有當您需要立即清除所有歷程記錄資料表中的過時資料列，請使用此預存程序。 您應該知道，它就可以有減輕資料庫記錄檔和 I/O 子系統有重大的影響，因為它會刪除所有合格的資料列，在相同交易內。 

一律建議依賴清除內部背景工作移除過時的資料列，以盡可能不影響正常的工作負載和一般的資料庫。

## <a name="permissions"></a>Permissions  
 需要 db_owner 權限。  

## <a name="example"></a>範例

```
declare @rowcnt int
EXEC sys.sp_cleanup_temporal_history 'dbo', 'Department', @rowcnt output
select @rowcnt
```

## <a name="see-also"></a>另請參閱

[時態表保留原則](https://docs.microsoft.com/azure/sql-database/sql-database-temporal-tables-retention-policy)
