---
title: 管理密碼 (AccessToSQL) |Microsoft 文件
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: b099d0f9-dd37-4c87-8b6f-ed0177881ea4
caps.latest.revision: 13
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 52b9f120a7025905630ffcf9762f4ce46b6abf52
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2018
---
# <a name="managing-passwords-accesstosql"></a>管理密碼 (AccessToSQL)
本節是關於保護資料庫的密碼和匯入或將它們匯出到伺服器的程序：  
  
1.  保護密碼  
  
2.  匯出或匯入加密的密碼  
  
## <a name="securing-password"></a>保護密碼  
SSMA 可讓您保護您的資料庫的密碼。  
  
您可以使用下列程序來實作安全的連線：  
  
指定有效的密碼，使用下列三種方法之一：  
  
1.  **純文字：** 'password' 節點的值屬性中輸入資料庫密碼。 在指令碼檔案或伺服器連接檔案的 [伺服器] 區段的伺服器定義節點底下找到它。  
  
    以純文字密碼不安全。 因此，您將會遇到下列警告訊息中的主控台輸出： *"伺服器&lt;伺服器識別碼&gt;密碼會提供不安全的純文字形式 SSMA 主控台應用程式提供的選項來保護密碼加密，請參閱說明檔的詳細資訊的 SSMA – securepassword 選項。 」*  
  
    **加密的密碼：**指定的密碼，在此情況下，是以加密形式儲存 ProtectedStorage.ssma 在本機電腦。  
  
    -   **保護密碼**  
  
        -   執行`SSMAforAccessConsole.exe`與`–securepassword`，並在命令列傳遞伺服器包含伺服器定義一節中的密碼 節點的連接或指令碼檔案中新增參數。  
  
        -   在提示字元中輸入資料庫密碼並確認它被要求使用者。  
  
            伺服器定義識別碼和其相對應的加密的密碼會儲存在本機電腦上的檔案  
  
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
  
        執行`SSMAforAccessConsole.exe`與`–securepassword`和`–remove`在將伺服器識別碼，若要移除加密的密碼從本機電腦上存在的受保護的儲存體檔案傳遞的命令列參數。  
  
            C:\SSMA\SSMAforAccessConsole.EXE –securepassword –remove all
            C:\SSMA\SSMAforAccessConsole.EXE –securepassword –remove "source_1,target_1"  
  
    -   **列出其密碼加密的伺服器識別碼**  
  
        執行與 SSMAforAccessConsole.exe`–securepassword`和`–list`切換在命令列，列出所有已加密密碼的伺服器識別碼。  
  
            C:\SSMA\SSMAforAccessConsole.EXE –securepassword –list  
  
    > [!NOTE]  
    > 1.  以指令碼或伺服器的連接檔案中所述的純文字密碼會優先於受保護的檔案中的加密密碼。  
    > 2.  當沒有密碼存在於伺服器連接檔案或指令碼檔案的 [伺服器] 區段中，或它有未受保護本機電腦上，主控台會提示您輸入的密碼。  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>匯出或匯入加密的密碼  
SSMA 主控台應用程式可讓您將加密的資料庫密碼存在於本機電腦上的檔案中匯出至受保護的檔案，反之亦然。 它可協助進行獨立的加密的密碼的電腦。 匯出功能會讀取伺服器識別碼及密碼從本機受保護的儲存體，並將資訊儲存在加密的檔案。 系統會提示使用者輸入受保護檔案的密碼。 請確定輸入的密碼長度 8 個字元以上。 此受保護的檔案分散到不同的電腦是可攜式的。 匯入功能讀取受保護的檔案從伺服器識別碼和密碼資訊。 使用者就會提示輸入密碼的受保護的檔案，並將資訊附加到本機受保護的儲存體。  


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
[執行 SSMA 主控台 (Access)](http://msdn.microsoft.com/en-us/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
