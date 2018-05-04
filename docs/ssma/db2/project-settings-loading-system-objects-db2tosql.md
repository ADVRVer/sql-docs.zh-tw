---
title: 專案設定 （載入系統物件） (DB2ToSQL) |Microsoft 文件
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9a545233-1b0a-488a-a1ec-c33aa608dcc1
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 996027fcd919c4689ba3971c618f045b0759c994
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="project-settingsloading-system-objects-db2tosql"></a>專案設定 （載入系統物件） (DB2ToSQL)
[載入系統物件] 頁面的**專案設定** 對話方塊可讓您指定的 DB2 系統物件 SSMA 會將轉換和載入[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]。  
  
[載入系統物件] 窗格位於**專案設定**和**預設專案設定**對話方塊：  
  
-   若要指定所有的 SSMA 專案設定**工具**功能表上，選取**預設專案設定**，選取移轉專案類型，不需要檢視或變更設定**移轉的目標版本**下拉式清單按一下**一般**左的窗格中，然後再按一下底部**載入系統物件**。  
  
-   若要指定目前的專案中，設定**工具**功能表上，選取**專案設定**，按一下 **一般**左的窗格中，然後再按一下底部**載入系統物件**。  
  
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
  
如果您的 DB2 物件參考其他系統物件，您應該選取這些物件。 如果您未選取您的 DB2 資料庫物件所參考的系統物件，SSMA 會報告轉換錯誤。 如果您收到因遺漏的系統物件的轉換錯誤，請在此對話方塊中選取遺漏的物件。 接著，您可以重複視需要轉換。  
  
