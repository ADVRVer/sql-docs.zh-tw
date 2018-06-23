---
title: MSSQLSERVER_3452 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b6ef54d9a48826e67d1fbf8b3673a590a2c58962
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36137318"
---
# <a name="mssqlserver3452"></a>MSSQLSERVER_3452
    
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|3452|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|REC_CHECKIDENTITY|  
|訊息文字|資料庫 '%.*ls' (%d) 的復原偵測到資料表識別碼 %d 中的識別值可能不一致。 請執行 DBCC CHECKIDENT ('%.\*ls')。|  
  
## <a name="explanation"></a>說明  
 升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 時，復原資料庫中識別值的處理序在中繼資料中發現不一致的問題。  
  
## <a name="user-action"></a>使用者動作  
 執行 DBCC CHECKIDENT。  
  
  