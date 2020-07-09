---
title: MSSQLSERVER_2530 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 76ad2670dc60665fa128dd97aa335330228262ef
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780350"
---
# <a name="mssqlserver_2530"></a>MSSQLSERVER_2530
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細資料  
  
| 屬性 | 值 |  
| :-------- | :---- |  
|產品名稱|SQL Server|  
|事件識別碼|2530|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|DBCC_INDEX_IS_OFFLINE|  
|訊息文字|資料表 "%.\*ls" 上的索引 "%.*ls" 已停用。|  
  
## <a name="explanation"></a>說明  
指定的索引已停用，因此無法進行 SQL 陳述式。 索引停用後，在重建或卸除並重新建立之前，索引會一直維持在停用狀態。  
  
## <a name="user-action"></a>使用者動作  
  
1.  使用以下其中一個方法來啟用已停用的索引：  
  
    -   ALTER INDEX 陳述式加上 REBUILD 子句  
  
    -   CREATE INDEX 加上 DROP_EXISTING 子句  
  
    -   DBCC DBREINDEX  
  
2.  請重新執行 DBCC 陳述式。  
  
## <a name="see-also"></a>另請參閱  
[啟用索引和條件約束](~/relational-databases/indexes/enable-indexes-and-constraints.md)  
[ALTER INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/alter-index-transact-sql.md)  
[CREATE INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/create-index-transact-sql.md)  
[DBCC DBREINDEX &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-dbreindex-transact-sql.md)  
  
