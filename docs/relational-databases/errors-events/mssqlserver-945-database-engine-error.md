---
description: MSSQLSERVER_945
title: MSSQLSERVER_945 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2bd18aad57eed6596ff83fc5fddbb50d33cba49a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420892"
---
# <a name="mssqlserver_945"></a>MSSQLSERVER_945
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細資料  
  
| 屬性 | 值 |  
| :-------- | :---- |  
|產品名稱|SQL Server|  
|事件識別碼|945|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|DB_IS_SHUTDOWN|  
|訊息文字|檔案無法存取、記憶體或磁碟空間不足，因此無法開啟資料庫 '%.*ls'。  詳細資訊請參閱 SQL Server 錯誤記錄檔。|  
  
## <a name="explanation"></a>說明  
資料庫無法存取，因為遺失檔案或其他資源。  
  
## <a name="user-action"></a>使用者動作  
檢查錯誤記錄檔，以取得有關記憶體、磁碟空間或權限失敗的詳細資訊。 確認受影響資料庫的 .mdf 和 .ndf 檔案位置，並確認 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 所使用的帳戶有權限可以存取這些檔案。 更正問題之後，使用 ALTER DATABASE 將資料庫設定為 ONLINE，以重新啟動資料庫。  
  
