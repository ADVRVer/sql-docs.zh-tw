---
title: sys.databases identity_columns （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- identity_columns
- sys.identity_columns
- sys.identity_columns_TSQL
- identity_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.identity_columns catalog view
ms.assetid: 97ee01e6-9c9e-4fd9-884b-68b4084669d5
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c663e45a462619ecbee8889a91f996025827da6c
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86011639"
---
# <a name="sysidentity_columns-transact-sql"></a>sys.identity_columns (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  針對每個識別欄位，各包含一個資料列。  
  
 [ **Identity_columns** ] 視圖會繼承 [sys.databases] 視圖中的資料**列**。 **Identity_columns**視圖會傳回 [ **sys.databases** ] 視圖中的資料行，再加上 [ **seed_value**]、[ **increment_value**]、[ **last_value**] 和 [ **is_not_for_replication** ] 資料行。 如需詳細資訊，請參閱[目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**\<columns inherited from sys.columns>**||[ **Sys.databases] identity_columns**視圖會傳回 [ **sys.databases** ] 視圖中的所有資料行。 另外亦將傳回以下所述的其他資料行。 如需**sys. identity_columns** view 繼承自**sys.databases**之資料行的描述，請參閱[sys.databases &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)。|  
|**seed_value**|**sql_variant**|這個識別欄位的初始值。 初始值的資料類型，與資料行本身的資料類型相同。|  
|**increment_value**|**sql_variant**|這個識別欄位的遞增值。 初始值的資料類型，與資料行本身的資料類型相同。|  
|**last_value**|**sql_variant**|這個識別欄位的最終值。 初始值的資料類型，與資料行本身的資料類型相同。|  
|**is_not_for_replication**|**bit**|識別欄位被宣告為 NOT FOR REPLICATION。 **注意：** 此資料行不適用於 Azure Synapse 分析。|  
  
> [!NOTE]  
>  若要建立可用於多個資料表中或可在不參考任何資料表的情況下從應用程式進行呼叫的自動遞增數字，請參閱 [序號](../../relational-databases/sequence-numbers/sequence-numbers.md)。  
  
## <a name="permissions"></a>權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的物件目錄檢視](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [&#40;Transact-sql&#41;的目錄檢視](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [查詢 SQL Server 系統目錄 FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
