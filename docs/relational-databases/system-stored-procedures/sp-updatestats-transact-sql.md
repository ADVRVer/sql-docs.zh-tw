---
title: sp_updatestats (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 09/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_updatestats_TSQL
- sp_updatestats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_updatestats
ms.assetid: 01184651-6e61-45d9-a502-366fecca0ee4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 51fd5471ac678a1d61986aaa9219eec923c38485
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535760"
---
# <a name="spupdatestats-transact-sql"></a>sp_updatestats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

執行`UPDATE STATISTICS`針對目前資料庫中的所有使用者定義和內部資料表。  
  
如需詳細資訊`UPDATE STATISTICS`，請參閱 < [UPDATE STATISTICS &#40;TRANSACT-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)。 如需統計資料的詳細資訊，請參閱[統計資料](../../relational-databases/statistics/statistics.md)。  
    
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
sp_updatestats [ [ @resample = ] 'resample']  
```  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="arguments"></a>引數  
`[ @resample = ] 'resample'` 指定**sp_updatestats**將使用的 RESAMPLE 選項[UPDATE STATISTICS](../../t-sql/statements/update-statistics-transact-sql.md)陳述式。 如果 **'resample'** 未指定，則**sp_updatestats**使用預設取樣來更新統計資料。 **resample**已**varchar(8)** 預設值為 [否]。  
  
## <a name="remarks"></a>備註  
 **sp_updatestats**會執行`UPDATE STATISTICS`，藉由指定`ALL`關鍵字，在資料庫中的所有使用者定義和內部資料表上。 sp_updatestats 會顯示進度訊息。 當更新完成時，它會報告已更新所有資料表的統計資料。  
  
sp_updatestats 會針對停用的非叢集索引更新統計資料，但不會針對停用的叢集索引更新統計資料。  
  
對於以磁碟為基礎的資料表，請**sp_updatestats**更新統計資料基礎**modification_counter**中的資訊**sys.dm_db_stats_properties**目錄檢視，正在更新至少一個資料列已經過修改的統計資料。 執行時，一律會更新記憶體最佳化資料表上的統計資料**sp_updatestats**。 因此不會執行**sp_updatestats**超過必要。  
  
**sp_updatestats**可以觸發重新編譯的預存程序或其他已編譯的程式碼。 不過， **sp_updatestats**可能不會導致重新編譯，如果只有一個查詢計畫為所參考的資料表和索引。 在這些情況下，重新編譯是不必要的，即使已更新統計資料也一樣。  
  
資料庫相容性層級低於 90，執行**sp_updatestats**不會保留特定統計資料的最新 NORECOMPUTE 設定。 對於相容性層級為 90 或更高版本的資料庫，sp_updatestats 就會保留特定統計資料的最新 NORECOMPUTE 選項。 如需停用及重新啟用統計資料更新的詳細資訊，請參閱[統計資料](../../relational-databases/statistics/statistics.md)。  
  
## <a name="permissions"></a>Permissions  
 需要的成員資格**sysadmin**固定伺服器角色或資料庫擁有權 (**dbo**)。  

## <a name="examples"></a>範例  
下列範例會更新 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中之資料表的統計資料。  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_updatestats;   
```  

## <a name="automatic-index-and-statistics-management"></a>自動索引與統計資料管理
利用[自適性索引重組](https://github.com/Microsoft/tigertoolbox/tree/master/AdaptiveIndexDefrag)等解決方案，為一或多個資料庫自動管理索引重組以及統計資料更新。 這項程序會根據索引分散程度與其他參數，自動選擇要進行重建或是重新組織索引，並以線性閾值更新統計資料。

## <a name="see-also"></a>另請參閱  
 [ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_autostats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_createstats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [系統預存程序](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
 
