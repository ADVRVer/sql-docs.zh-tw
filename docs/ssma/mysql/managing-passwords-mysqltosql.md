---
title: 管理密碼（MySQLToSQL） |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 07/06/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Password management, importing or exporting encrypted password
- Password management, securing password
ms.assetid: 4ffbc587-ea3f-49ad-bc42-a654f672325e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: fc06af58a8e669b836a88490ebcbc7c971ca2f4f
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053554"
---
# <a name="managing-passwords-mysqltosql"></a>管理密碼 (MySQLToSQL)
本文說明如何保護資料庫密碼，以及在伺服器之間匯入或匯出的程式。
  
## <a name="securing-password"></a>保護密碼  
SSMA 可讓您保護資料庫的密碼。  
  
使用下列程式來執行安全連線：  
  
使用下列三種方法的其中一種來指定有效的密碼：  
  
1.  **純文字：** 在 [密碼] 節點的 [值] 屬性中輸入資料庫密碼。 它位於腳本檔案或伺服器連接檔案之 [伺服器] 區段的 [伺服器定義] 節點底下。  
  
    純文字的密碼並不安全。 因此，您將會在主控台輸出中遇到下列警告訊息：「*伺服器 &lt; 伺服器識別碼 &gt; 密碼以非安全純文字格式提供」，SSMA 主控台應用程式提供選項來透過加密來保護密碼，請參閱 SSMA 說明檔中的-securepassword 選項以取得詳細資訊。* 」  
  
    **加密的密碼：** 在此情況下，指定的密碼會以加密格式儲存在 ProtectedStorage. ssma 中的本機電腦上。  
  
    -   **保護密碼**  
  
        -   在 `SSMAforMySQLConsole.exe` `-securepassword` 命令列上，使用並新增參數來執行，並在伺服器定義區段中傳遞包含密碼節點的伺服器連接或腳本檔案。  
  
        -   出現提示時，系統會要求使用者輸入資料庫密碼並加以確認。  
  
            伺服器定義識別碼及其對應的加密密碼會儲存在本機電腦上的檔案中  
            
            **範例 1：**
            
            1. 指定密碼
            
            2. `C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -add all -s "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ VariableValueFileSample.xml"`
            
            3. 輸入 server_id ' XXX_1 ' 的密碼： xxxxxxx
            
            4. 重新輸入 server_id ' XXX_1 ' 的密碼： xxxxxxx
            
            **範例 2：**
            
            1. `C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -add "source_1,target_1" -c "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ServersConnectionFileSample.xml" - v "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ VariableValueFileSample.xml" -o`
            
            2. 輸入 server_id ' source_1 ' 的密碼： xxxxxxx
            
            3. 重新輸入 server_id ' source_1 ' 的密碼： xxxxxxx
            
            4. 輸入 server_id ' target_1 ' 的密碼： xxxxxxx
            
            5. 重新輸入 server_id ' target _1 ' 的密碼： xxxxxxx
            
    -   **移除加密的密碼**  
  
        `SSMAforMySQLConsole.exe` `-securepassword` `-remove` 在命令列上使用和參數執行，傳遞伺服器識別碼，以從本機電腦上的受保護儲存體檔案移除加密的密碼。  
  
        範例：  

        ```console
        C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -remove all
        C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -remove "source_1,target_1"  
        ```
  
    -   **列出其密碼已加密的伺服器識別碼**  
  
        使用在 `SSMAforMySQLConsole.exe` `-securepassword` `-list` 命令列上執行並切換，以列出其密碼已加密的所有伺服器識別碼。  
  
        範例：  
        
        ```console
        C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -list  
        ```
  
    > [!NOTE]  
    > 1.  腳本或伺服器連接檔案中所述的純文字密碼，其優先順序高於安全檔案中的加密密碼。  
    > 2.  如果伺服器連接檔案或腳本檔案的 [伺服器] 區段中沒有任何密碼，或是本機電腦上未受保護，則主控台會提示您輸入密碼。  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>匯出或匯入加密的密碼  
SSMA 主控台應用程式可讓您將本機電腦上檔案中的加密資料庫密碼，匯出至受保護的檔案，反之亦然。 這有助於讓加密的密碼獨立于電腦上。

匯出功能會從本機受保護的儲存體讀取伺服器識別碼和密碼，並將資訊儲存在加密的檔案中。 系統會提示使用者輸入受保護檔案的密碼。 請確定輸入的密碼長度為8個字元或更多。 這個受保護的檔案可在不同的電腦上攜帶。

匯入功能會從受保護的檔案讀取伺服器識別碼和密碼資訊。 系統會提示使用者輸入受保護檔案的密碼，並將資訊附加到本機受保護的存放裝置。  
  
### <a name="export-example"></a>匯出範例：  

1. 匯出密碼

2. 輸入密碼以保護匯出的檔案

3. C:\SSMA\SSMAforMySQLConsole.EXE-securepassword-全部匯出 "machine1passwords"

4. 輸入密碼以保護匯出的檔案： xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

5. 請確認密碼： xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

6. C:\SSMA\SSMAforMySQLConsole.EXE-p-e "MySQLDB_1_1，Sql_1" "machine2passwords. file"

7. 輸入密碼以保護匯出的檔案： xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

8. 請確認密碼： xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx  
  
### <a name="import-example"></a>匯入範例：  

1. 匯入加密的密碼

2. 輸入密碼以保護匯入的檔案

3. C:\SSMA\SSMAforMySQLConsole.EXE-securepassword-匯入所有 "machine1passwords"

4. 輸入密碼以從加密的檔案匯入伺服器： xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

5. 請確認密碼： xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

6. C:\SSMA\SSMAforMySQLConsole.EXE-p-i "MySQLDB_1，Sql_1" "machine2passwords. file"

7. 輸入密碼以從加密的檔案匯入伺服器： xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

8. 請確認密碼： xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx  
  
## <a name="see-also"></a>另請參閱  
[執行 SSMA 主控台（MySQL）](https://msdn.microsoft.com/e3e9f7e4-0619-4861-a202-3d5d39953b26)  
  
