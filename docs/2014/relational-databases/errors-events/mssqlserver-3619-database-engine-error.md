---
title: MSSQLSERVER_3619 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3619 (Database Engine error)
ms.assetid: 7d94f8d9-65ca-4fde-9c17-7b83e94a3779
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6a82902d69a1d5214b29f43d19ded58c76293ec4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2020
ms.locfileid: "62914024"
---
# <a name="mssqlserver_3619"></a>MSSQLSERVER_3619
    
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|3619|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|SYS_NOLOG|  
|訊息文字|無法在資料庫識別碼 %d 中寫入檢查點記錄，因為記錄空間不足。 請連絡資料庫管理員截斷記錄，或者配置更多的空間給資料庫記錄檔。|  
  
## <a name="explanation"></a>說明  
 交易記錄磁碟空間不足。  
  
## <a name="user-action"></a>使用者動作  
 截斷記錄以釋出部分空間，或配置更多空間給記錄檔。 如需詳細資訊，請參閱《SQL Server 線上叢書》中的＜寫滿交易記錄疑難排解 (錯誤 9002)＞。  
  
  
