---
title: sys.databases assembly_modules （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.assembly_modules
- sys.assembly_modules_TSQL
- assembly_modules
- assembly_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assembly_modules catalog view
ms.assetid: 5f9e644e-8065-49a2-b53d-db7df98f70d8
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 967626693c52cc31bacddf88735224f3e191e6a6
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829177"
---
# <a name="sysassembly_modules-transact-sql"></a>sys.assembly_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  針對由 Common Language Runtime (CLR) 組件定義的每個函數、程序或觸發程序，各傳回一個資料列。 這個目錄檢視會將 CLR 預存程序、CLR 觸發程序或 CLR 函數對應至它們的基本實作。 TA、AF、PC、FS 和 FT 類型的物件，各有相關聯的組件模組。 若要找出物件與組件之間的關聯，可以將這個目錄檢視合併到其他目錄檢視。 例如，當您建立 CLR 預存程式時，它會以**sys.databases**中的一個資料清單示， **sys** . procedure 中的一個資料列（繼承自**sys.databases**），而一個資料列在**sys.databases 中 assembly_modules**。 預存程式本身是以**sys.databases**和**sys.databases**中的中繼資料來表示。 程式的基礎 CLR 實作為參考，可在 sys.databases 中找到**assembly_modules**。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|SQL 物件的物件識別碼。 在資料庫中，這是唯一的。|  
|**assembly_id**|**int**|建立這個模組所用之組件的識別碼。|  
|**assembly_class**|**sysname**|定義這個模組之組件內的類別名稱。|  
|**assembly_method**|**sysname**|定義此模組之**assembly_class**中的方法名稱。<br /><br /> 如果是彙總函式 (AF)，則為 NULL。|  
|**null_on_null_input**|**bit**|模組宣告的目的不是為了因應任何 NULL 輸入而產生 NULL 輸出。|  
|**execute_as_principal_id**|**int**|執行內容所用的資料庫主體識別碼，由 CLR 函數、預存程序或觸發程序的 EXECUTE AS 子句所指定。<br /><br /> NULL = EXECUTE AS CALLER。 此為預設值。<br /><br /> 指定之資料庫主體 = EXECUTE AS SELF、EXECUTE AS *user_name*或 execute as *login_name*的識別碼。<br /><br /> -2 = EXECUTE AS OWNER。|  
  
## <a name="permissions"></a>權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的物件目錄檢視](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
