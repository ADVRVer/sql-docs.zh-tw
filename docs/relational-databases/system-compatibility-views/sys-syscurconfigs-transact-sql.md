---
title: sys.syscurconfigs （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.syscurconfigs
- sys.syscurconfigs_TSQL
- syscurconfigs
- syscurconfigs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.syscurconfigs compatibility view
- syscurconfigs system table
ms.assetid: 454ab849-07a5-4b50-ba0a-6b1b14721f77
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a20b7f5a4630d23942b6e1be15d8ff67e2d0b0e
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85901168"
---
# <a name="syssyscurconfigs-transact-sql"></a>sys.syscurconfigs (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  包含每個目前組態選項各一個項目。 同時，此檢視表含有描述組態結構的四個項目。 **syscurconfigs**是由使用者進行查詢時動態建立的。 如需詳細資訊，請參閱[sys.sys設定 &#40;transact-sql&#41;](../../relational-databases/system-compatibility-views/sys-sysconfigures-transact-sql.md)。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**value**|**int**|使用者可以修改的變數值。 只有在執行 RECONFIGURE 時，[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 才會使用這個項目。|  
|**config**|**smallint**|組態變數號碼。|  
|**加以**|**nvarchar(255)**|組態選項的說明。|  
|**status**|**smallint**|指出選項狀態的點陣圖。 可能的值如下：<br /><br /> 0 = 靜態。 設定在伺服器重新啟動時生效。<br /><br /> 1 = 動態。 變數在執行 RECONFIGURE 陳述式時生效。<br /><br /> 2 = 進階。 只有在已設定**show advanced 選項**時，才會顯示變數。<br /><br /> 3 = 動態和進階。|  
  
## <a name="see-also"></a>另請參閱  
 [將系統資料表對應至系統檢視 &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [相容性檢視 &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
