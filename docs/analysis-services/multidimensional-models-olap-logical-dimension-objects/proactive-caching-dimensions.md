---
title: 主動式快取 （維度） |Microsoft 文件
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: db9b77c799f674b39f3c6a66a6812464896abefc
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="proactive-caching-dimensions"></a>主動式快取 (維度)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  主動式快取會提供自動 MOLAP 快取建立及 OLAP 物件的管理。 Cube 會根據從資料庫接收而來的通知，立即併入對資料庫資料所做的變更。 主動式快取的目標是要提供傳統 MOLAP 的效能，同時保持 ROLAP 所提供的立即性與便於管理性。  
  
 簡單的 <xref:Microsoft.AnalysisServices.ProactiveCaching> 物件是由時間指定和資料表通知所組成。 時間指定會定義在收到變更通知以後，用於更新快取的時間範圍。 資料表通知會定義在資料表與 <xref:Microsoft.AnalysisServices.ProactiveCaching> 物件之間的通知結構描述。  
  
  
