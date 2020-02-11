---
title: sys.databases time_zone_info （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 08/06/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.time_zone_info
- sys.time_zone_info_TSQL
- time_zone_info
- time_zone_info_TSQL
helpviewer_keywords:
- sys.time_zone_info system table
ms.assetid: 3f51a9a4-75f8-4a11-9552-8bf6118b68da
author: stevestein
ms.author: sstein
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 69bfcbb7e1eeaf6b456a2e10d1f3bfcc581c3d76
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106697"
---
# <a name="systime_zone_info-transact-sql"></a>sys.databases time_zone_info （Transact-sql）
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  傳回支援時區的相關資訊。 電腦上安裝的所有時區都儲存在下列登錄區中：  
`KEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones`.  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|採用 Windows 標準格式的時區名稱。 例如，**澳大利亞中部標準時間**或**中歐標準時間**。|  
|**current_utc_offset**|**Nvarchar （12）**|UTC 的目前位移。 例如， **+ 01:00**或 **-07:00**。|  
|**is_currently_dst**|**bit**|如果目前觀察日光節約時間，則為 True。|  
  
## <a name="see-also"></a>另請參閱  
 [GETUTCDATE &#40;Transact-sql&#41;](../../t-sql/functions/getutcdate-transact-sql.md)   
 [在時區 &#40;Transact-sql&#41;](../../t-sql/queries/at-time-zone-transact-sql.md)   
 [日期和時間資料類型和函數 &#40;Transact-sql&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [&#40;Transact-sql&#41;的伺服器範圍設定目錄檢視](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)  
