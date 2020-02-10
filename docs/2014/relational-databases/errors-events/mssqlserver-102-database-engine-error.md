---
title: MSSQLSERVER_102 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 102 (Database Engine error)
ms.assetid: 264dc1a2-c8a0-4c89-b5f6-951baf950299
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ee88ba8a77602fd50412669f96e1e16ddcdd37c7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "62870736"
---
# <a name="mssqlserver_102"></a>MSSQLSERVER_102
    
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|102|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|P_SYNTAXERR2|  
|訊息文字|接近 '%.*ls' 的語法不正確。|  
  
## <a name="explanation"></a>說明  
 表示語法錯誤。 因為錯誤讓 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 無法處理陳述式，所以無法取得其他資訊。  
  
 可能導因於嘗試使用已被取代的 RC4 或 RC4_128 加密建立一組對稱金鑰，但不是在相容性模式 90 或 100 之中。  
  
## <a name="user-action"></a>使用者動作  
 在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式中搜尋語法錯誤。  
  
 若使用 RC4 或 RC4_128 建立對稱金鑰，請選取較新的加密方式，例如其中一種 AES 演算法 (建議使用)。若必須使用 RC4，請使用 ALTER DATABASE SET COMPATIBILITY_LEVEL 將資料庫相容性層級設為 90 或 100 (不建議使用)。  
  
  
