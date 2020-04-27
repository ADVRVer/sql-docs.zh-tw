---
title: sys.databases fn_trace_gettable （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_trace_gettable
- fn_trace_gettable_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_trace_gettable function
- sys.fn_trace_gettable function
ms.assetid: c2590159-6ec5-4510-81ab-e935cc4216cd
author: rothja
ms.author: jroth
ms.openlocfilehash: 18a6225bca9539f10c4dfea61e99d147cb188d4c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2020
ms.locfileid: "68059217"
---
# <a name="sysfn_trace_gettable-transact-sql"></a>sys.fn_trace_gettable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  以表格式格式傳回一個或多個追蹤檔的內容。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 請改用擴充事件。  
   
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
fn_trace_gettable ( 'filename' , number_files )  
```  
  
## <a name="arguments"></a>引數  
 '*filename*'  
 指定所要讀取的初始追蹤檔。 *filename*是**Nvarchar （256）**，沒有預設值。  
  
 *number_files*  
 指定要讀取的換用檔案的數目。 此數目包括*filename*中指定的初始檔案。 *number_files*為**int**。  
  
## <a name="remarks"></a>備註  
 如果*number_files*指定為**預設值**， **fn_trace_gettable**會讀取所有換用檔案，直到到達追蹤結尾為止。 **fn_trace_gettable**會傳回資料表，其中包含對指定追蹤有效的所有資料行。 如需詳細資訊，請參閱[sp_trace_setevent &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)。  
  
 請注意，fn_trace_gettable 函數不會載入換用檔案（使用*number_files*引數指定此選項時），其中原始追蹤檔案名的結尾是底線和數值。 （這不適用於在檔案變換時自動附加的底線和數位）。因應措施是，您可以將追蹤檔案重新命名，以移除原始檔案名稱中的底線。 例如，如果原始檔案名為**Trace_Oct_5 .trc** ，而換用檔案的名稱為**Trace_Oct_5_1 .trc**，則您可以將檔案重新命名為**TraceOct5. .trc**和**TraceOct5_1. .trc**。  
  
 這個函數可以讀取在執行它的執行個體中仍然有效的追蹤。  
  
## <a name="permissions"></a>權限  
 需要伺服器的 ALTER TRACE 權限。  
  
## <a name="examples"></a>範例  
  
### <a name="a-using-fn_trace_gettable-to-import-rows-from-a-trace-file"></a>A. 使用 fn_trace_gettable 匯入追蹤檔的資料列  
 下列範例會在 `fn_trace_gettable` 陳述式的 `FROM` 子句中呼叫 `SELECT...INTO`。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * INTO temp_trc  
FROM fn_trace_gettable('c:\temp\mytrace.trc', default);  
GO  
```  
  
### <a name="b-using-fn_trace_gettable-to-return-a-table-with-an-identity-column-that-can-be-loaded-into-a-sql-server-table"></a>B. 使用 fn_trace_gettable 傳回內含可以載入 SQL Server 資料表之 IDENTITY 資料行的資料表  
 下列範例會在 `SELECT...INTO` 陳述式中呼叫這個函數，且會傳回一份含有可載入 `IDENTITY` 資料表之 `temp_trc` 資料行的資料表。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT IDENTITY(int, 1, 1) AS RowNumber, * INTO temp_trc  
FROM fn_trace_gettable('c:\temp\mytrace.trc', default);  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_trace_generateevent &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
  
