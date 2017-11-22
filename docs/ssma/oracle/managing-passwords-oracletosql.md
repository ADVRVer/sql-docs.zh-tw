---
title: "管理密碼 (OracleToSQL) |Microsoft 文件"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Managing Passwords in Oracle, Exporting or Importing Encrypted Password
- Managing passwords in Oracle, Securing Password
ms.assetid: 8c7d9f8e-06bb-476c-bbd2-15b61d5bba3c
caps.latest.revision: "24"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 1360c23595b7ff81180352795f0a78ded3efd583
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="managing-passwords-oracletosql"></a>管理密碼 (OracleToSQL)
本節是關於保護資料庫的密碼和匯入或將它們匯出到伺服器的程序：  
  
1.  保護密碼  
  
2.  匯出或匯入加密的密碼  
  
## <a name="securing-password"></a>保護密碼  
SSMA 可讓您保護您的資料庫的密碼。  
  
您可以使用下列程序來實作安全的連線：  
  
指定有效的密碼，使用下列三種方法之一：  
  
1.  **純文字：** 'password' 節點的值屬性中輸入資料庫密碼。 在指令碼檔案或伺服器連接檔案的 [伺服器] 區段的伺服器定義節點底下找到它。  
  
    以純文字密碼不安全。 因此，您將會遇到下列警告訊息中的主控台輸出： *"伺服器&lt;伺服器識別碼&gt;密碼是不安全的純文字形式 SSMA 主控台應用程式提供的選項來保護透過加密的密碼，請參閱 – securepassword 選項的詳細資訊的 SSMA 說明檔中提供。"*  
  
    **加密的密碼：**指定的密碼，在此情況下，是以加密形式儲存 ProtectedStorage.ssma 在本機電腦。  
  
    -   **保護密碼**  
  
        -   執行`SSMAforOracleConsole.exe`與`–securepassword`，並在命令列傳遞伺服器包含伺服器定義一節中的密碼 節點的連接或指令碼檔案中新增參數。  
  
        -   在提示字元中輸入資料庫密碼並確認它被要求使用者。  
  
            伺服器定義識別碼和其相對應的加密的密碼會儲存在本機電腦上的檔案  
            
            範例 1：  
            
                Specify password
                
                C:\SSMA\SSMAforOracleConsole.EXE –securepassword –add all –s "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\AssessmentReportGenerationSample.xml" –v "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx
            
            範例 2：
            
                C:\SSMA\SSMAforOracleConsole.EXE –securepassword –add "source_1,target_1" –c "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ServersConnectionFileSample.xml" – v "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx  
    
    -   **移除加密的密碼**  
  
        執行`SSMAforOracleConsole.exe`與`–securepassword`和`–remove`在將伺服器識別碼，若要移除加密的密碼從本機電腦上存在的受保護的儲存體檔案傳遞的命令列參數。  
        
        範例：  
        
            C:\SSMA\SSMAforOracleConsole.EXE –securepassword –remove all
            C:\SSMA\SSMAforOracleConsole.EXE –securepassword –remove "source_1,target_1"  
  
    -   **列出其密碼加密的伺服器識別碼**  
  
        執行`SSMAforOracleConsole.exe`與`–securepassword`和`–list`切換在命令列，列出所有已加密密碼的伺服器識別碼。  
  
        範例：  
        
            C:\SSMA\SSMAforOracleConsole.EXE –securepassword –list  
  
    > [!NOTE]  
    > 1.  以指令碼或伺服器的連接檔案中所述的純文字密碼會優先於受保護的檔案中的加密密碼。  
    > 2.  當沒有密碼存在於伺服器連接檔案或指令碼檔案的 [伺服器] 區段中，或它有未受保護本機電腦上，主控台會提示您輸入的密碼。  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>匯出或匯入加密的密碼  
SSMA 主控台應用程式可讓您將加密的資料庫密碼存在於本機電腦上的檔案中匯出至受保護的檔案，反之亦然。 它可協助進行獨立的加密的密碼的電腦。 匯出功能會讀取伺服器識別碼及密碼從本機受保護的儲存體，並將資訊儲存在加密的檔案。 系統會提示使用者輸入受保護檔案的密碼。 請確定輸入的密碼長度 8 個字元以上。 此受保護的檔案分散到不同的電腦是可攜式的。 匯入功能讀取受保護的檔案從伺服器識別碼和密碼資訊。 使用者就會提示輸入密碼的受保護的檔案，並將資訊附加到本機受保護的儲存體。  
  
範例：  

    Export password
    
    Enter password for protecting the exported file C:\SSMA\SSMAforOracleConsole.EXE –securepassword –export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforOracleConsole.EXE –p –e "OracleDB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
範例：  

    Import an encrypted password
    
    Enter password for protecting the imported file C:\SSMA\SSMAforOracleConsole.EXE –securepassword –import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforOracleConsole.EXE –p –i "OracleDB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
## <a name="see-also"></a>請參閱＜  
[執行 SSMA 主控台 (Oracle)](http://msdn.microsoft.com/en-us/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  
