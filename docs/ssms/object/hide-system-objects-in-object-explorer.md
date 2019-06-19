---
title: 在物件總管中隱藏系統物件 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- hiding system objects
- system objects [SQL Server]
- objects [SQL Server], hiding
- Object Explorer, hiding objects
ms.assetid: c01d8804-838c-4f75-b78c-80e41e4fffdc
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 5b36198aba754f8424e29ba529fe936516213cad
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "65102934"
---
# <a name="hide-system-objects-in-object-explorer"></a>在物件總管中隱藏系統物件
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 [物件總管] 中隱藏系統物件。 物件總管的 [資料庫] 節點包含諸如系統資料庫的系統物件。 使用 [工具]/[選項] 頁面，隱藏系統物件。 某些系統物件 (如系統函數和系統資料類型) 不受這個設定所影響。  
  
## <a name="SSMSProcedure"></a>使用 SQL Server Management Studio  
  
#### <a name="to-hide-system-objects-in-object-explorer"></a>若要在物件總管中隱藏系統物件  
  
1.  在 **[工具]** 功能表上，按一下 **[選項]**。  
  
2.  在 [環境/啟動] 頁面上，選取 [在物件總管中隱藏系統物件]，然後按一下 [確定]。  
  
3.  在 [SQL Server Management Studio] 對話方塊中，按一下 [確定]，以確認必須重新啟動 SQL Server Management Studio，這個變更才會生效。  
  
4.  關閉並重新開啟 SQL Server Management Studio。  
  
