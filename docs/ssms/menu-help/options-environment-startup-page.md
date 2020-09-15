---
description: 選項 ([環境] - [啟動] 頁面)
title: " SQL Server [選項] 頁面 - [環境] - [啟動]"
ms.date: 11/05/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 85d0b99d0929f7fb7ae642c5b0673fdc7b9b185b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88417904"
---
# <a name="options-environment---startup-page"></a>選項 ([環境] - [啟動] 頁面)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

使用 [選項]  對話方塊來設定 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的啟動動作、一般視窗管理選項，以及其他一般設定。 在 [工具]  功能表上按一下 [選項]  ，展開 [環境]  資料夾，然後按一下 [啟動]  。

## <a name="ui-element-list"></a>UI 元素清單

**啟動時**

選取 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 啟動時要執行的動作。 可用選項包括：

- [開啟物件總管]  會提示進行連接，然後開啟物件總管。

- [開啟新增查詢視窗]  會提示進行連接，然後開啟 SQL 查詢編輯器。

- [開啟物件總管和查詢視窗]  會提示進行連線，然後使用該連線開啟 [物件總管] 和 [SQL 查詢編輯器]。

- [開啟物件總管和活動監視器]

- [開啟空白環境]  會開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，但沒有 SQL 查詢編輯器視窗，且不會將物件總管連接到伺服器。

**在 [物件總管] 中隱藏系統物件**

選取此核取方塊，即可從 [物件總管] 中的樹狀檢視裡，移除系統資料庫、系統資料表、系統檢視，以及系統預存程序。 系統函數與系統資料類型並未隱藏。 此選項僅適用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，且不會影響在 [物件總管] 中已經連接的伺服器。

## <a name="see-also"></a>另請參閱

- [選項對話方塊 F1 說明](options-dialog-boxes-f1-help.md)
- [選項 (環境 - 一般頁面)](options-environment-general-page.md)
