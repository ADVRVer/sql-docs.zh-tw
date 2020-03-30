---
title: SQL Server 單元測試的自訂測試條件
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: 32a15d61-e908-4ae1-a238-4fd0f988d8c8
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 2852d075b6d5b1f55b76fea6b32443ea14e74384
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "75245525"
---
# <a name="custom-test-conditions-for-sql-server-unit-tests"></a>SQL Server 單元測試的自訂測試條件

您可以新增 SQL Server 單元測試的自訂測試條件。 不過，無論您已建立擴充功能或要安裝其他人建立的擴充功能，都必須先安裝測試條件，才能使用它。  
  
安裝不是您建立的測試條件之前，必須了解下列風險：  
  
-   測試條件的安裝程式可能是惡意程式，會根據您的安裝權限存取受保護的資源。  
  
-   測試條件本身可能是惡意的，如果使用擴充功能的使用者有足夠的權限，它就會取得受保護資源的控制權。  
  
為了降低風險，只在自訂測試條件來自已知來源時，才予以安裝。 如果您從未受信任的來源取得測試條件，應該檢查該測試條件的原始程式碼及其安裝程式 (如果有)，然後進行安裝。  
  
若要安裝自訂測試條件，請將已簽署的組件 (.dll) 複製到 %Program Files%\Microsoft Visual Studio <Version>\Common7\IDE\Extensions\Microsoft\SQLDB\TestConditions 資料夾。 如果這個資料夾不存在，則予以建立。 您需要電腦的系統管理權限，才能複製到這個目錄。  
  
> [!NOTE]  
> 在下列情況下，您需要安裝 Visual Studio 2010 和 Visual Studio 2012 版的測試條件：  
>   
> -   您在可用來建置 SQL Server 單元測試的電腦上，安裝自訂測試條件。  
> -   這些單元測試可用於 Visual Studio 2010 和 Visual Studio 2012。  
  
如需 SQL Server 單元測試之自訂測試條件的詳細資訊，請參閱：  
  
-   [如何：建立 SQL Server 單元測試設計工具的測試條件](../ssdt/how-to-create-test-conditions-for-the-sql-server-unit-test-designer.md)  
  
-   [如何：將 Visual Studio 2010 自訂測試條件從舊版升級至 SQL Server Data Tools](../ssdt/how-to-upgrade-visual-studio-2010-custom-test-condition-to-ssdt.md)  
  
-   [逐步解說：使用自訂測試條件來驗證預存程序的結果](../ssdt/walkthrough-use-custom-test-condition-to-verify-stored-procedure-results.md)  
  
## <a name="see-also"></a>另請參閱  
[使用 SQL Server 單元測試驗證資料庫程式碼](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)  
  
