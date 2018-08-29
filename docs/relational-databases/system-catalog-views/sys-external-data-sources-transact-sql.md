---
title: sys.external_data_sources & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1016db6e-9950-4ae2-a004-bd4171e27359
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6dec76073fbd0a6e0ed7da85dd247f3435dec85b
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43064926"
---
# <a name="sysexternaldatasources-transact-sql"></a>sys.external_data_sources & Amp;#40;transact-SQL&AMP;#41;
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  包含目前資料庫中每個外部資料來源的資料列[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]， [!INCLUDE[ssSDS](../../includes/sssds-md.md)]，和[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]。  
  
 包含每個外部資料來源的伺服器上的一個資料列[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]。  
  
|資料行名稱|資料類型|描述|範圍|  
|-----------------|---------------|-----------------|-----------|  
|data_source_id|**int**|外部資料來源的物件識別碼。||  
|NAME|**sysname**|外部資料來源的名稱。||  
|location|**nvarchar(4000)**|連接字串，其中包括通訊協定、 IP 位址和外部資料來源的連接埠。||  
|type_desc|**nvarchar(255)**|資料來源類型顯示為字串。|HADOOP，RDBMS，SHARD_MAP_MANAGER RemoteDataArchiveTypeExtDataSource|  
|型別|**tinyint**|表示為數字顯示的資料來源類型。|0-HADOOP<br /><br /> 1 - RDBMS<br /><br /> 2-SHARD_MAP_MANAGER<br /><br /> 3 - RemoteDataArchiveTypeExtDataSource|  
|resource_manager_location|**nvarchar(4000)**|如需輸入 HADOOP、 IP 和連接埠的 Hadoop 資源管理員位置。 這用來提交 Hadoop 資料來源上的作業。<br /><br /> 其他類型的外部資料來源為 NULL。||  
|credential_id|**int**|資料庫的物件識別碼範圍用來連接到外部資料來源的認證。||  
|database_name|**sysname**|類型的 RDBMS 中，遠端資料庫的名稱。 對於類型，SHARD_MAP_MANAGER，分區對應管理員資料庫的名稱。 其他類型的外部資料來源為 NULL。||  
|shard_map_name|**sysname**|類型 SHARD_MAP_MANAGER，分區對應的名稱。 其他類型的外部資料來源為 NULL。||  
  
## <a name="permissions"></a>Permissions  
 目錄檢視內中繼資料的可見性會限制在使用者所擁有的安全性實體，或已授與使用者某些權限的安全性實體。 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [sys.external_file_formats &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)   
 [sys.external_tables &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-catalog-views/sys-external-tables-transact-sql.md)   
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)  
  
  
