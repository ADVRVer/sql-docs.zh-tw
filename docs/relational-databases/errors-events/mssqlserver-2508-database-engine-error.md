---
title: MSSQLSERVER_2508 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 2508 (Database Engine error)
ms.assetid: c37d40e5-c665-4d66-a727-5cb845634fcc
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 37a5f8976dabed380173dc56bb99edd07daec4df
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2018
ms.locfileid: "34320609"
---
# <a name="mssqlserver2508"></a>MSSQLSERVER_2508
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|2508|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT|  
|訊息文字|物件 "%.\*ls"，索引識別碼 %d，分割區識別碼 %I64d，配置單位識別碼 %I64d (類型 %.\*ls) 的 %.*ls 計數不正確。 請執行 DBCC UPDATEUSAGE。|  
  
## <a name="explanation"></a>說明  
在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 版本中，資料表和索引資料列計數值與頁數計數值可能會變得不正確。 在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 之前的版本中建立的資料庫可能包含不正確的計數。 DBCC CHECKDB 已經增強為可以偵測到這些錯誤，而且會在遇到錯誤時傳回這則警告訊息。  
  
## <a name="user-action"></a>使用者動作  
針對指定的物件或索引，或針對包含此物件的資料庫執行 DBCC UPDATEUSAGE，以便更正無效的計數。  
  
