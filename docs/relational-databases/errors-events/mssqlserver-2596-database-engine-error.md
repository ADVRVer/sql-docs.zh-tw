---
title: MSSQLSERVER_2596 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 2596 (Database Engine error)
ms.assetid: 49ab892f-8ba3-4ba1-b562-ddf205019802
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 8eb8b851b589c916a449b527c8037e932d683472
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver2596"></a>MSSQLSERVER_2596
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|2596|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|DBCC_DATABASE_IN_READ_ONLY_MODE|  
|訊息文字|未處理修復陳述式。 資料庫不可以是唯讀模式。|  
  
## <a name="explanation"></a>說明  
此訊息指出資料庫為唯讀模式。 當資料庫處於唯讀模式時，便無法進行修復。  
  
## <a name="user-action"></a>使用者動作  
使用 ALTER DATABASE 將資料庫設定成讀取/寫入，然後重新執行 DBCC 命令。  
  
## <a name="see-also"></a>另請參閱  
[ALTER DATABASE &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql-set-options.md)  
  
