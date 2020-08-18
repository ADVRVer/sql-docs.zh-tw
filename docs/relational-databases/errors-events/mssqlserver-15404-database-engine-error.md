---
description: MSSQLSERVER_15404
title: MSSQLSERVER_15404 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 15404 (Database Engine error)
ms.assetid: 69677f02-bc81-4e4a-99b8-5c1bd1de36df
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a9a05c8e47e97357b562a3429b98fe856e60d75f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88333854"
---
# <a name="mssqlserver_15404"></a>MSSQLSERVER_15404
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細資料  
  
| 屬性 | 值 |  
| :-------- | :---- |  
|產品名稱|SQL Server|  
|事件識別碼|15404|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|SEC_NTGRP_ERROR|  
|訊息文字|無法獲得關於 Windows NT 群組/使用者 '*user*' 的資訊，錯誤碼 *code*。|  
  
## <a name="explanation"></a>說明  
如果指定的是無效的主體，驗證時會使用 15404。 或者，因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶和 Windows 帳戶的網域之間沒有完全信任關係，所以 Windows 帳戶模擬失敗。  
  
## <a name="user-action"></a>使用者動作  
請確定 Windows 主體存在，並且沒有拼字錯誤。  
  
如果這個錯誤是因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶和 Windows 帳戶的網域之間缺少完全信任關係，則採取下列其中一個動作就能解決問題：  
  
-   使用與 Windows 使用者位於相同網域的帳戶來執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。  
  
-   如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是使用電腦帳戶 (例如「網路服務」或「本機系統」)，則這部電腦必須受到包含 Windows 使用者的網域信任。  
  
-   使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶。  
  
