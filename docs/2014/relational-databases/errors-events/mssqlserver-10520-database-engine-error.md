---
title: MSSQLSERVER_10520 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c6cdc100429aa8c0cca55261679cdae1c5ebd66e
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554173"
---
# <a name="mssqlserver_10520"></a>MSSQLSERVER_10520
    
## <a name="details"></a>詳細資料  
  
|屬性|值|  
|-|-|  
|產品名稱|SQL Server|  
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
  
  
