---
title: MSSQLSERVER_21898 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 21898 (Database Engine error)
ms.assetid: 02405b21-3d4e-4c2d-b4b3-d7b1ec05edb4
caps.latest.revision: 6
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: fbed13bbcedcc0bb39791663ba5d13525215d84b
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver21898"></a>MSSQLSERVER_21898
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|21898|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|SQLErrorNum21898|  
|訊息文字|發行者 '%s' 使用散發資料庫 '%s' 而不是 '%s'，但若要主控發行資料庫 '%s' 必須使用後者。 請在散發者 '%s' 上執行 **sp_changedistpublisher**，以將發行者所使用的散發資料庫變更為 '%s'。|  
  
## <a name="explanation"></a>說明  
**sp_validate_redirected_publisher** 會查詢位於本機散發者的 msdb.dbo.MSdistpublishers，以確認新發行者所使用的散發資料庫是否與原始發行者所使用的散發資料庫相同。 當這些資料庫不同時，就會傳回此錯誤，讓發行者不適合當做發行者資料庫的主機。  
  
## <a name="user-action"></a>使用者動作  
請執行 **sp_changedistpublisher** 預存程序，將新發行者的散發資料庫變更為原始發行者所使用的散發資料庫。  
  
> [!NOTE]  
> 在發行者的散發者上執行 **sp_adddistpublisher** 時，如果輸入了錯誤的散發資料庫，執行 **sp_changedistpublisher** 便可解決問題。 不過，如果遠端發行者的現有發行集來自使用已識別散發資料庫的另一個發行資料庫，這項變更則不適用。 您必須有系統地移除使用具名散發資料庫的複寫，然後再使用原始發行者的散發資料庫來重新建立複寫，才能讓新的發行者當做適合的主機。  
  

