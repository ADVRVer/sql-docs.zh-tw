---
title: MSSQLSERVER_10520 | Microsoft Docs
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
- 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 07a9561564711ce37e6e1867b81870341d7b5e45
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36023989"
---
# <a name="mssqlserver10520"></a>MSSQLSERVER_10520
    
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|10520|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|PG_PARAM_NOT_ALLOWED|  
|訊息文字|無法建立計畫指南 '%.*ls'，因為已將 @type 指定為 '%ls'，而且已為參數 '%ls' 指定非 NULL 值， 但這種類型要求參數必須為 NULL 值。 請為參數指定 NULL，或將參數類型變更為允許非 NULL 值的類型。|  
  
## <a name="explanation"></a>說明  
 在 @type 中指定的類型要求指定的參數必須為 NULL 值，但是卻提供了非 NULL 值。  
  
## <a name="user-action"></a>使用者動作  
 請為參數指定 NULL，或將參數類型變更為允許非 NULL 值的類型。  
  
## <a name="see-also"></a>另請參閱  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [計畫指南](../performance/plan-guides.md)  
  
  
