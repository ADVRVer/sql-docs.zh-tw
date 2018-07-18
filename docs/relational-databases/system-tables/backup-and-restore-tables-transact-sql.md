---
title: 備份與還原資料表 (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system tables [SQL Server], backup tables
- backup system tables [SQL Server]
- system tables [SQL Server], restore tables
- restore system tables [SQL Server]
ms.assetid: aa615add-54e6-40f5-8b55-3728b26884ee
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 09a35a516808c5330199cd60f1e9dbde9192d004
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38003031"
---
# <a name="backup-and-restore-tables-transact-sql"></a>備份及還原資料表 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  本節中的主題介紹儲存資料庫備份與還原作業所用的資訊之系統資料表。  
  
## <a name="in-this-section"></a>本節內容  
 [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md)  
 針對資料庫的每個資料或記錄檔，各包含一個資料列。  
  
 [backupfilegroup](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)  
 針對備份時在資料庫中的每個檔案群組，各包含一個資料列。  
  
 [backupmediafamily](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)  
 針對每個媒體家族，各包含一個資料列。  
  
 [backupmediaset](../../relational-databases/system-tables/backupmediaset-transact-sql.md)  
 每個備份組各含一個資料列。  
  
 [backupset](../../relational-databases/system-tables/backupset-transact-sql.md)  
 每個備份組各含一個資料列。  
  
 [logmarkhistory](../../relational-databases/system-tables/logmarkhistory-transact-sql.md)  
 針對已認可的每個標示交易，各包含一個資料列。  
  
 [restorefile](../../relational-databases/system-tables/restorefile-transact-sql.md)  
 針對每個還原的檔案，各包含一個資料列。 其中包括檔案群組名稱間接還原的檔案。  
  
 [restorefilegroup](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)  
 針對每個還原的檔案群組，各包含一個資料列。  
  
 [restorehistory](../../relational-databases/system-tables/restorehistory-transact-sql.md)  
 每項還原作業都有一個資料列。  
  
 [suspect_pages](../../relational-databases/system-tables/suspect-pages-transact-sql.md)  
 針對每個失敗並出現 824 錯誤 (限制為 1,000 個資料列) 的頁面，各包含一個資料列。  
  
 [sysopentapes](../../relational-databases/system-tables/sysopentapes-transact-sql.md)  
 針對目前開啟的每個磁帶裝置，各包含一個資料列。  
  
  
