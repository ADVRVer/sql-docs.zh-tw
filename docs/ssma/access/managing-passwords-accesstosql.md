---
title: 管理密碼 (AccessToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: b099d0f9-dd37-4c87-8b6f-ed0177881ea4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d0a0f167f14910f657f6c65b9778b0aadde65b10
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51664207"
---
# <a name="managing-passwords-accesstosql"></a>管理密碼 (AccessToSQL)
本章節是關於保護資料庫的密碼和匯入，或將它們匯出到伺服器的程序：  
  
1.  保護密碼  
  
2.  匯出或匯入加密的密碼  
  
## <a name="securing-password"></a>保護密碼  
SSMA 可讓您保護您的資料庫的密碼。  
  
您可以使用下列程序來實作安全的連線：  
  
指定有效的密碼，使用下列三種方法之一：  
  
1.  **純文字格式：** 'password' 節點的值屬性中輸入資料庫密碼。 在指令碼檔案或伺服器連線檔案伺服器一節中的伺服器定義節點底下找到。  
  
    以純文字密碼並不安全的。 因此，您會遇到下列警告訊息中的主控台輸出： *「 伺服器&lt;伺服器識別碼&gt;密碼會提供不安全的純文字形式 SSMA 主控台應用程式會提供選項，以保護透過加密的密碼，請參閱說明檔，如需詳細資訊在 SSMA 中的 – securepassword 選項。 」*  
  
    **加密的密碼：** 指定的密碼，在此情況下，是以加密形式儲存 ProtectedStorage.ssma 在本機電腦上。  
  
    -   **保護密碼**  
  
        -   執行`SSMAforAccessConsole.exe`與`–securepassword`，並在命令列傳遞伺服器包含伺服器定義一節中的 [密碼] 節點的連接或指令碼檔案中新增參數。  
  
        -   在提示字元中輸入資料庫密碼並確認它會要求使用者。  
  
            伺服器定義識別碼和其對應的加密的密碼會儲存在本機電腦上的檔案  
  
            範例 1：
            
                Specify password
                
                C:\SSMA\SSMAforAccessConsole.EXE –securepassword –add all –s "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml" –v "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx  
            
            範例 2：
            
                C:\SSMA\SSMAforAccessConsole.EXE –securepassword –add "source_1,target_1" –c "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml" – v "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx  
  
    -   **移除加密的密碼**  
  
        執行`SSMAforAccessConsole.exe`具有`–securepassword`和`–remove`參數在命令列傳遞的伺服器識別碼，若要移除本機電腦上存在的受保護的儲存體檔案加密的密碼。  
  
            C:\SSMA\SSMAforAccessConsole.EXE –securepassword –remove all
            C:\SSMA\SSMAforAccessConsole.EXE –securepassword –remove "source_1,target_1"  
  
    -   **列出其密碼加密的伺服器識別碼**  
  
        執行與 SSMAforAccessConsole.exe`–securepassword`和`–list`參數在命令列，以列出所有已加密密碼的伺服器識別碼。  
  
            C:\SSMA\SSMAforAccessConsole.EXE –securepassword –list  
  
    > [!NOTE]  
    > 1.  指令碼或伺服器連線檔案中所述的純文字密碼的優先於受保護的檔案中的加密密碼。  
    > 2.  當沒有密碼存在於伺服器連線檔案或指令碼檔案的 [伺服器] 區段中，或它有未受保護本機電腦上，主控台會提示您輸入的密碼。  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>匯出或匯入加密的密碼  
SSMA 主控台應用程式可讓您將加密的資料庫密碼存在於本機電腦上的檔案匯出至受保護的檔案，反之亦然。 這有助於讓加密的密碼機器無關。 匯出功能會讀取伺服器識別碼和密碼從本機保護的儲存體，並將資訊儲存在加密的檔案。 系統會提示使用者輸入受保護檔案的密碼。 請確定輸入的密碼是 8 個字元長度，或多個項目。 此受保護的檔案在不同電腦是可攜式的。 匯入功能讀取受保護的檔案從伺服器 id 和密碼資訊。 使用者會提示輸入密碼的受保護的檔案，並將資訊附加到本機受保護的儲存體。  


    Export password
    
    Enter password for protecting the exported file
    
    C:\SSMA\SSMAforAccessConsole.EXE –securepassword –export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforAccessConsole.EXE –p –e "AccessDB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  


    Import an encrypted password
    
    Enter password for protecting the imported file
    
    C:\SSMA\SSMAforAccessConsole.EXE –securepassword –import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforAccessConsole.EXE –p –i "AccessDB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
## <a name="see-also"></a>另請參閱  
[執行 SSMA 主控台 （存取）](https://msdn.microsoft.com/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
