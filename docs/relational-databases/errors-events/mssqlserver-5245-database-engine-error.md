---
description: MSSQLSERVER_5245
title: MSSQLSERVER_5245 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 67ae97cdfc3e6db07870844e418eacc07c4c857f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470983"
---
# <a name="mssqlserver_5245"></a>MSSQLSERVER_5245
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細資料  
  
| 屬性 | 值 |  
| :-------- | :---- |  
|產品名稱|SQL Server|  
|事件識別碼|5245|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED|  
|訊息文字|物件識別碼 O_ID (物件 'NAME')：DBCC 無法在此物件上取得鎖定，因為已超過鎖定要求逾時期間。 已經略過這個物件，不會處理。|  
  
## <a name="explanation"></a>說明  
DBCC 等候指定物件的資料表鎖定時發生鎖定逾時。  
  
## <a name="user-action"></a>使用者動作  
重新執行 DBCC 命令。  
  
