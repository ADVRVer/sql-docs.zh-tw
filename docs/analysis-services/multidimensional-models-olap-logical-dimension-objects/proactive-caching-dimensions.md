---
title: "主動式快取 （維度） |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- dimensions [Analysis Services], proactive caching
- proactive caching [Analysis Services]
ms.assetid: 7d57fe93-6e5f-4a50-844f-dd2bbdbb94a5
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 619a731b497f40cb359d61e5fa0c4d987d1fae72
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="proactive-caching-dimensions"></a>主動式快取 (維度)
  主動式快取會提供自動 MOLAP 快取建立及 OLAP 物件的管理。 Cube 會根據從資料庫接收而來的通知，立即併入對資料庫資料所做的變更。 主動式快取的目標是要提供傳統 MOLAP 的效能，同時保持 ROLAP 所提供的立即性與便於管理性。  
  
 簡單的 <xref:Microsoft.AnalysisServices.ProactiveCaching> 物件是由時間指定和資料表通知所組成。 時間指定會定義在收到變更通知以後，用於更新快取的時間範圍。 資料表通知會定義在資料表與 <xref:Microsoft.AnalysisServices.ProactiveCaching> 物件之間的通知結構描述。  
  
  

