---
description: sp_help_fulltext_catalog_components (Transact-SQL)
title: sp_help_fulltext_catalog_components (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_catalog_components_TSQL
- sp_help_fulltext_catalog_components
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_catalog_components
ms.assetid: fbd6a3d4-6a4c-42a2-bff8-2a5eb0745e47
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2884cda986a99f23c88c71c8960d25a467de0663
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89548018"
---
# <a name="sp_help_fulltext_catalog_components-transact-sql"></a>sp_help_fulltext_catalog_components (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  傳回目前資料庫中所有全文檢索目錄所用的所有元件 (篩選、斷詞工具和通訊協定處理常式) 的清單。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_help_fulltext_catalog_components  
```  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**全文檢索目錄名稱**|**int**|全文檢索目錄的名稱。|  
|**全文檢索目錄識別碼**|**sysname**|全文檢索目錄的識別碼。|  
|**componenttype**|**sysname**|這是元件的類型， 下列其中之一：<br /><br /> 篩選<br /><br /> 通訊協定處理常式<br /><br /> 斷詞工具|  
|**componentname**|**sysname**|元件的名稱。|  
|**Clsid**|**uniqueidentifier**|元件的類別識別碼。|  
|**fullpath**|**nvarchar(256)**|元件位置的路徑。<br /><br /> Null = 呼叫端不是 **serveradmin** 固定伺服器角色的成員。|  
|**version**|**nvarchar(30)**|元件的版本。|  
|**製造商**|**sysname**|元件的製造商名稱。|  
  
## <a name="permissions"></a>權限  
 需要 **public** 角色的成員資格。  
  
## <a name="see-also"></a>另請參閱  
 [全文檢索搜尋和語義搜尋預存程式 &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)   
 [sys.fulltext_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [sp_help_fulltext_system_components &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md)   
 [全文檢索搜尋](../../relational-databases/search/full-text-search.md)  
  
  
