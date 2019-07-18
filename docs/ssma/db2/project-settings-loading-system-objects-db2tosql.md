---
title: 專案設定 （載入系統物件） (DB2ToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9a545233-1b0a-488a-a1ec-c33aa608dcc1
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 5c12a2ddb97c6d599e5adfc57277e0a5f64288e5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68060195"
---
# <a name="project-settingsloading-system-objects-db2tosql"></a>專案設定 （載入系統物件） (DB2ToSQL)
正在載入系統物件的頁數**專案設定** 對話方塊可讓您指定的 DB2 系統物件 SSMA 會將轉換和載入[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
[載入系統物件] 窗格位於**專案設定**並**預設專案設定**對話方塊：  
  
-   若要指定所有的 SSMA 專案設定**工具**功能表上，選取**預設專案設定**，選取 移轉專案類型，則需要可以檢視或變更設定**移轉的目標版本**下拉式清單按一下**一般**在底部的左的窗格中，然後按一下**載入系統物件**。  
  
-   若要指定目前的專案中，設定**工具**功能表上，選取**專案設定**，按一下 **一般**底部的左窗格中，然後按一下  **載入系統物件**。  
  
## <a name="default-settings"></a>預設值  
系統物件的轉換會耗用系統資源，並花的時間。 若要改善效能，SSMA 只選取最常使用的系統物件，如下列清單所示：  
  
-   SYS.DBMS_OUTPUT  
  
-   SYS.DBMS_PIPE  
  
-   SYS.DBMS_UTILITY  
  
-   SYS。標準  
  
-   SYS.UTL_FILE  
  
-   SYS.DBMS_LOB  
  
-   SYS.DBMS_SQL  
  
-   SYS.DBMS_SESSION  
  
如果您的 DB2 物件參考其他的系統物件，您應該選取這些物件。 如果您未選取 DB2 資料庫物件所參考的系統物件，SSMA 會報告轉換錯誤。 如果您收到因遺漏的系統物件的轉換錯誤，請在這個對話方塊中選取遺失的物件。 接著，您可以重複視需要轉換。  
  
