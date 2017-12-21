---
title: "啟用記憶體選項中的鎖定頁面 (Windows) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Lock Pages in Memory option
ms.assetid: cd581fbc-4747-439e-87f9-2f18e39c5bb9
caps.latest.revision: "35"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: b5758fcbb5e73e40a3022d5a97fb744b6735c7d2
ms.sourcegitcommit: 4a462c7339dac7d3951a4e1f6f7fb02a3e01b331
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2017
---
# <a name="enable-the-lock-pages-in-memory-option-windows"></a>啟用鎖定記憶體分頁選項 (Windows)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] 此 Windows 原則決定哪些帳戶可以使用處理序將資料保留在實體記憶體中，以防止系統將資料分頁到磁碟上的虛擬記憶體。  
  
> [!NOTE]  
>  在預期到磁碟的分頁記憶體時，在記憶體中鎖定分頁可能會提升效能。  
  
 請使用 Windows 群組原則工具 (gpedit.msc)，以針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所使用的帳戶啟用這個原則。 您必須是系統管理員，才可變更這個原則。  
  
### <a name="to-enable-the-lock-pages-in-memory-option"></a>若要啟用鎖定記憶體分頁選項  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。 在 [開啟舊檔] 方塊中，輸入 **gpedit.msc**。  
  
2.  在 [本機群組原則編輯器] 主控台中，依序展開 [電腦設定] 和 [Windows 設定]。  
  
3.  展開 [安全性設定]，然後展開 [本機原則]。  
  
4.  選取 [使用者權限指派] 資料夾。  
  
     這些原則會顯示在詳細資料窗格中。  
  
5.  在窗格中按兩下 [鎖定記憶體中的分頁]。  
  
6.  在 [本機安全性設定 – 鎖定記憶體中的分頁] 對話方塊中，按一下 [新增使用者或群組]。  
  
7.  在 [選取使用者、服務帳戶或群組] 對話方塊中，加入具有執行 sqlservr.exe 權限的帳戶。  
  
8.  重新啟動 SQL Server Data Engine 服務，這項設定才會生效。
  
## <a name="see-also"></a>另請參閱  
 [伺服器記憶體伺服器組態選項](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
  
