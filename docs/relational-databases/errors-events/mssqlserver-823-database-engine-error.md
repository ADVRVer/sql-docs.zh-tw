---
title: MSSQLSERVER - Database Engine 錯誤 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 823 (Database Engine error)
ms.assetid: 0d9fce3c-3772-46ce-a7a3-4f4988dc6cae
caps.latest.revision: 24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 879077ad0440edb4b0f6d65c3087d309a8e225e7
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2018
ms.locfileid: "34326139"
---
# <a name="mssqlserver---database-engine-error"></a>MSSQLSERVER - Database Engine 錯誤
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|823|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|B_HARDERR|  
|訊息文字|作業系統將錯誤 %ls 傳回給 SQL Server，期間：%S_MSG 在 %#016I64x 位移，檔案：'%ls'。 SQL Server 錯誤記錄檔和系統事件記錄檔中的訊息或許可以提供其他詳細資訊。 這是嚴重的系統層級錯誤狀況，且可能會損及資料庫的完整性，所以必須立即更正。 請執行完整的資料庫一致性檢查 (DBCC CHECKDB)。 導致這個錯誤的原因有許多可能性; 如需詳細資訊，請參閱《SQL Server 線上叢書》。|  
  
## <a name="explanation"></a>說明  
Windows 讀取或寫入要求失敗。 Windows 傳回的錯誤碼和對應的文字都已插入訊息中。 在讀取案例中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已經重試讀取要求四次。 這個錯誤通常是硬體錯誤所造成的結果，但也可能是裝置驅動程式所引起的。 如需錯誤 823 的詳細資訊，請參閱 [http://support.microsoft.com/kb/828339](http://support.microsoft.com/kb/828339)。 如需 I/O 錯誤的詳細資訊，請參閱[Microsoft SQL Server I/O Basics, Chapter 2](http://go.microsoft.com/fwlink/?LinkId=69370) (第 2 章 Microsoft SQL Server I/O 基本概念)。  
  
## <a name="user-action"></a>使用者動作  
查看系統事件記錄檔中的其他資訊， 並連絡硬體製造商或 Microsoft 客戶服務及支援中心，確定其原因與更正動作。 更正硬體錯誤之後，請還原所有資料庫並執行 DBCC CHECKDB。  
  
