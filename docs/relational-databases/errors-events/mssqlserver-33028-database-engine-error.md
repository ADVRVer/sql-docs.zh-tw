---
title: MSSQLSERVER_33028 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 33028 (Database Engine error)
ms.assetid: c5cec0e4-0bcd-4907-826f-e7d835cfcb37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ae11fbccaa4f577815e503d9a0dffaa34c7c04ed
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723612"
---
# <a name="mssqlserver_33028"></a>MSSQLSERVER_33028
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細資料  
  
| 屬性 | 值 |  
| :-------- | :---- |  
|產品名稱|SQL Server|  
|事件識別碼|33028|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|SEC_CRYPTOPROV_CANTOPENSESSION|  
|訊息文字|無法為 %S_MSG '%.*ls' 開啟工作階段。 提供者錯誤碼: %d。|  
  
## <a name="explanation"></a>說明  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 無法開啟錯誤訊息中所列的密碼編譯提供者。 此密碼編譯提供者提供了所列的錯誤碼。 如需有關此錯誤的詳細資訊，您可能必須連絡密碼編譯提供者。  
  
|錯誤碼|描述|  
|--------------|---------------|  
|0|成功。 沒有錯誤。|  
|1|失敗。 發生未指定或意外的錯誤。 沒有其他資訊可用。|  
|2|緩衝區不足。 無法針對密碼編譯提供者配置空間。|  
|3|不支援。 這個版本不支援此密碼編譯提供者。 請選取另一個密碼編譯提供者。|  
|4|找不到。 指定的密碼編譯提供者不存在，或者您沒有存取這些檔案的授權。|  
|5|授權失敗。 可能是因為在建立認證時提供了不正確的密碼或使用者名稱。 如果此認證不存在，也可能會造成這種情況。|  
|6|無效的引數。 將無效的引數傳遞給密碼編譯提供者。|  
  
## <a name="user-action"></a>使用者動作  
解決此錯誤，或者連絡密碼編譯提供者以了解詳細資訊。  
  
