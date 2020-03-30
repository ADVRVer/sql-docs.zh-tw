---
title: 關於文件中的程式碼範例 | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3f035c37-0f2e-47d4-94e0-a10774402e82
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dc76cee723c11d49a4d6149a7c3a1df4cedbc256
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "68015176"
---
# <a name="about-code-examples-in-the-documentation"></a>關於文件中的程式碼範例
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="remarks-about-the-code-examples"></a>程式碼範例的備註
執行 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 文件中的程式碼範例時，須留意幾項要點：  
  
-   幾乎所有範例都假設已在本機電腦上安裝 SQL Server 2008 或更新版本和 AdventureWorks 資料庫。  
  
    如需如何下載 SQL Server 免費版和試用版的相關資訊，請參閱 [SQL Server](https://go.microsoft.com/fwlink/?LinkID=120193)。  
  
    如需如何下載並安裝 AdventureWorks 資料庫的資訊，請參閱 [SQL Server 範例 GitHub 存放庫中的 AdventureWorks 頁面](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) \(英文\)。
  
-   本文件中幾乎所有的程式碼範例均應從命令列執行，如此可讓所有程式碼範例的測試自動化。 如需如何從命令列執行 PHP 的相關資訊，請參閱 [從命令列使用 PHP](https://php.net/manual/en/features.commandline.php)。  
  
-   雖然這些範例旨在從命令列執行，但每個範例都可以從瀏覽器叫用來執行，且無須對指令碼進行任何變更。 若要為輸出設定好看的格式，請將各範例中的每個 "\n" 取代為 "\<\/br>"，再從瀏覽器中加以叫用。  
  
-   為了讓每個範例專注在其重點上，我們並未在所有範例中執行正確的錯誤處理。 建議您檢查任何對 **sqlsrv** 函數或 PDO 方法的呼叫是否有錯誤，並根據應用程式的需求予以處理。  
  
    發生錯誤時，您可以透過下列程式碼行結束指令碼，以取得錯誤資訊：  
  
    ```  
    die( print_r( sqlsrv_errors(), true));  
    ```  
  
    或者，如果您使用 PDO，  
  
    ```  
    print_r ($stmt->errorInfo());  
    die();  
    ```  
  
    如需關於處理錯誤和警告的詳細資訊，請參閱 [處理錯誤和警告](../../connect/php/handling-errors-and-warnings.md)。  
  
## <a name="see-also"></a>另請參閱  
[Microsoft Drivers for PHP for SQL Server 概觀](../../connect/php/overview-of-the-php-sql-driver.md)
  
