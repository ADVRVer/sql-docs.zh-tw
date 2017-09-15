---
title: "加入 Visual FoxPro 資料來源 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual FoxPro data source [ODBC], adding
- adding data sources [ODBC], Visual FoxPro ODBC driver
ms.assetid: 1487e188-52c8-4f48-b4fe-25a650dd9e97
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d158cf38e5755e0e443d6cb47e4053bd05d45287
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="adding-a-visual-foxpro-data-source"></a>加入 Visual FoxPro 資料來源
若要存取 Visual FoxPro 資料從您的應用程式，您必須使用資料來源。 您可以建立資料來源，如下所示：  
  
-   應用程式，例如 Microsoft® Word、 Microsoft Excel 或 Microsoft Access 中，會使用 ODBC 驅動程式。  
  
-   應用程式之外使用 Microsoft Windows® 95、 Microsoft Windows 98、 或 Microsoft Windows/Windows 2000 控制台。  
  
 您的系統上不存在的資料來源之後，您可以重複使用相同的資料來源每當您想要存取 Visual FoxPro 資料。 如果您有數個不同的資料庫或您想要存取的資料表，您可以建立個別的資料來源的每個資料庫或目錄。  
  
 下列程序會使用控制台中，以建立資料來源。 如需如何從應用程式中建立資料來源的詳細資訊，請參閱[從 Microsoft Office 存取 Visual FoxPro 資料](../../odbc/microsoft/accessing-visual-foxpro-data-from-microsoft-office.md)。  
  
### <a name="to-add-a-visual-foxpro-data-source"></a>若要新增 Visual FoxPro 資料來源  
  
1.  執行 Windows 2000 的電腦上，開啟 Windows 控制台中，按兩下 系統管理工具。  
  
2.  按兩下資料來源 (ODBC) 若要開啟 ODBC 資料來源管理員 對話方塊。 您已安裝 Visual FoxPro ODBC 驅動程式或任何 ODBC 驅動程式軟體後，使用這個圖示。  
  
    > [!NOTE]  
    >  如果您執行舊版 Windows，請開啟 Windows 控制台中，然後按兩下 32 位元 ODBC 或 ODBC 若要開啟 ODBC 資料來源管理員 對話方塊。  
  
3.  按一下 [加入]。  
  
4.  在建立新的資料來源] 對話方塊中，選取 [Microsoft Visual FoxPro 驅動程式，然後按一下 [完成]。  
  
5.  在[ODBC Visual FoxPro 安裝程式對話方塊](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)輸入的資料來源名稱和描述，選取資料庫類型、 資料庫或目錄中，選取，然後按一下 [確定]。  
  
     新的資料來源名稱會顯示在 [使用者資料來源清單中的 ODBC 資料來源管理員] 對話方塊的 [使用者 DSN] 索引標籤。  
  
6.  按一下 [確定] 以儲存新的資料來源並關閉 [ODBC 資料來源管理員] 對話方塊。
