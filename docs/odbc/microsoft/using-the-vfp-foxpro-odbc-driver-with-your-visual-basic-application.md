---
title: "VFP FoxPro ODBC 驅動程式搭配 Visual Basic 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], visual basic applications
- Visual Basic applications [ODBC]
- FoxPro ODBC driver [ODBC], visual basic applications
- Visual FoxPro data [ODBC], visual basic applications
ms.assetid: 5223ca23-5df6-4ebc-aa3b-70682ff27a8c
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 266577d54e579956fcc2435283a9835c19f9ef36
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-the-vfp-foxpro-odbc-driver-with-your-visual-basic-application"></a>使用 VFP FoxPro ODBC 驅動程式與 Visual Basic 應用程式
您的 Microsoft® Visual Basic® 應用程式可以與 Visual FoxPro 資料通訊，藉由建立連接至 Visual FoxPro 資料來源的資料控制項。  
  
#### <a name="to-connect-to-visual-foxpro-data-using-the-data-control-in-visual-basic"></a>連接至 Visual FoxPro 資料 Visual Basic 中使用資料控制項  
  
1.  建立資料來源名稱為 「 測試 」 連接到包含在 Visual FoxPro TasTrade 範例資料庫。 Visual FoxPro 預設安裝位置中將 TasTrade 範例資料庫：  
  
    ```  
    c:\vfp\samples\mainsamp\data\tastrade.dbc  
    ```  
  
2.  在 Visual Basic 中建立新表單，並將文字方塊和資料控制項在其上。  
  
3.  變更資料控制項的連接屬性如下所示：  
  
    ```  
    ODBC;DATABASE=tastrade;DSN=test  
    ```  
  
4.  將記錄集類型 屬性變更為下列：  
  
    ```  
    2 - Snapshot  
    ```  
  
5.  將記錄來源 屬性變更為下列：  
  
    ```  
    customer  
    ```  
  
6.  將文字方塊中的資料來源屬性變更為下列資料控制項的預設名稱：  
  
    ```  
    data1  
    ```  
  
7.  將文字方塊的 DataField 屬性變更為下列：  
  
    ```  
    customer_id  
    ```  
  
8.  執行表單，並使用資料控制項可以跳過客戶識別碼欄位，從 Visual FoxPro TasTrade 範例資料庫。
