---
description: MSSQLSERVER_8649
title: MSSQLSERVER_8649 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7b599848c71b465d80c01eecd594f841ab5c0e72
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499436"
---
# <a name="mssqlserver_8649"></a>MSSQLSERVER_8649
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細資料  
  
| 屬性 | 值 |  
| :-------- | :---- |  
|產品名稱|SQL Server|  
|事件識別碼|8649|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|COST_TOO_HIGH|  
|訊息文字|查詢已經取消，因為這個查詢 (%d) 的預估成本超過了設定的臨界值 %d。 請連絡系統管理員。|  
  
## <a name="explanation"></a>說明  
由於查詢的預估成本超過了 QUERY_GOVERNOR_COST_LIMIT 設定的臨界值，因此已經取消查詢。  
  
## <a name="user-action"></a>使用者動作  
將 QUERY_GOVERNOR_COST_LIMIT 選項設定成較高的值。  
  
## <a name="see-also"></a>另請參閱  
[SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](~/t-sql/statements/set-query-governor-cost-limit-transact-sql.md)  
  
