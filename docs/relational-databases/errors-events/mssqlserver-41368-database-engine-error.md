---
title: MSSQLSERVER_41368 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
robots: noindex,nofollow
ms.workload: Inactive
ms.openlocfilehash: e2aded8bf29e77ff4239528790b3b8745dd97d3a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver41368"></a>MSSQLSERVER_41368
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|事件識別碼|41368|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED|  
|訊息文字|只有自動認可交易才支援使用 READ COMMITTED 隔離等級來存取記憶體最佳化的資料表。 明確或隱含交易則不支援。 為使用資料表提示例如 WITH (SNAPSHOT) 的記憶體最佳化資料表，提供支援的隔離等級。|  
  
## <a name="explanation"></a>說明  
只有自動認可交易支援使用 READ COMMITTED 隔離等級存取記憶體最佳化資料表。 如需詳細資訊，請參閱[與記憶體內部資料表及程序的交易](~/relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md)。  
  
如果您存取記憶體最佳化的資料表是透過以 BEGIN TRANSACTION 啟動的明確交易，或是透過 IMPLICIT_TRANSACTIONS 設為 ON 的隱含交易，便不支援 READ COMMITTED 隔離等級。  
  
## <a name="user-action"></a>使用者動作  
透過明確或隱含 READ COMMITTED 交易存取記憶體最佳化的資料表時，請使用快照集 (SNAPSHOT) 存取資料表。 這可透過使用資料表提示 WITH (SNAPSHOT) (如需詳細資訊，請參閱[與記憶體內部資料表及程序的交易](~/relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md))，或是將資料庫選項 MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT 設為 ON (如需詳細資訊，請參閱 [ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql.md)) 來達成。  
  
## <a name="see-also"></a>另請參閱  
[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
