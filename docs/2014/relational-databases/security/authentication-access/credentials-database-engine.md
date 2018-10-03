---
title: 認證 (Database Engine) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- principals [SQL Server], credentials
- schemas [SQL Server], credentials
- permissions [SQL Server], credentials
- groups [SQL Server], credentials
- ALTER ANY CREDENTIAL permission
- security [SQL Server], credentials
- authentication [SQL Server], credentials
- users [SQL Server], credentials
- credentials [SQL Server], about credentials
- credentials [SQL Server]
ms.assetid: c8df6022-e0b4-46b8-9670-3f86938d3177
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: d42f93735723c81baf837736bfabcda2b1707aae
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48144538"
---
# <a name="credentials-database-engine"></a>認證 (Database Engine)
  認證是包含驗證資訊 (認證) 的記錄，該項資訊是連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]外部資源時所需的資訊， 此資訊會由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]用於內部。 大部份認證都包含 Windows 使用者名稱和密碼。  
  
 儲存在認證中的資訊可讓透過 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的使用者，可以存取在伺服器執行個體外部的資源。 如果外部資源為 Windows，則使用者會驗證為認證中指定的 Windows 使用者。 單一認證可對應至多個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入。 但是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入只能對應至一個認證。  
  
 系統認證會自動建立並與特定端點關聯。 系統認證的名稱是以兩個雜湊符號 (##) 開頭。  
  
 如需有關認證的詳細資訊，請參閱 < [sys.credentials](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql)目錄檢視。  
  
## <a name="related-content"></a>相關內容  
 [建立認證](../authentication-access/create-a-credential.md)[建立認證&#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)  
  
 [保護 SQL Server 的安全](../securing-sql-server.md)  
  
  
