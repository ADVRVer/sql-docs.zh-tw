---
title: "部署 CLR 資料庫物件 |Microsoft 文件"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- deployment script [CLR integration]
- common language runtime [SQL Server], deploying
- deploying assemblies [CLR integration]
- deploying [CLR integration]
ms.assetid: 00752573-3367-41a7-af98-7b7a29e8e2f2
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ac5aa32532c32b3e3066dd4aa3c8cf575e1e83ff
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="deploying-clr-database-objects"></a>部署 CLR 資料庫物件
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
部署是指您用來散發即將在其他電腦上安裝和執行之已完成應用程式或模組的程序。 您可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 來開發 Common Language Runtime (CLR) 資料庫物件並將它們部署至測試伺服器。 或者，您也可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 轉散發檔案 (而非 Visual Studio) 來編譯 Managed 資料庫物件。 一旦編譯完成之後，您就可以使用 Visual Studio 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，將包含 CLR 資料庫物件的組件部署至測試伺服器。 請注意，Visual Studio .NET 2003 無法用於 CLR 整合程式設計或部署。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包含預先安裝的 .NET Framework，而且 Visual Studio .NET 2003 無法使用 .NET Framework 2.0 組件。  
  
 一旦 CLR 方法已經在測試伺服器上測試並驗證之後，您就可以使用部署指令碼，將它們散發至實際伺服器。 您可以手動產生部署指令碼，也可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來產生部署指令碼 (請參閱本主題後面的程序)。  
  
 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，CLR 整合功能預設是關閉的，而且您必須啟用此功能才能使用 CLR 組件。 如需詳細資訊，請參閱 [Enabling CLR Integration](../../relational-databases/clr-integration/clr-integration-enabling.md)。  
  
## <a name="deploying-the-assembly-to-the-test-server"></a>將組件部署至測試伺服器  
 您可以使用 Visual Studio 來開發 CLR 函數、程序、觸發程序、使用者定義型別 (UDT) 或使用者定義彙總 (UDA)，然後將它們部署至測試伺服器。 您也可以使用 .NET Framework 轉散發檔案隨附的命令列編譯器 (例如 csc.exe 和 vbc.exe) 來編譯這些 Managed 資料庫物件。 Visual Studio Integrated Development Environment 並非開發 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之 Managed 資料庫物件所需的條件。  
  
 請確定已解決所有編譯器錯誤和警告。 然後，您就可以使用 Visual Studio 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 陳述式，在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 資料庫中註冊包含 CLR 常式的組件。  
  
> [!NOTE]  
>  您必須在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上啟用 TCP/IP 網路通訊協定，才能針對遠端開發、偵錯和開發使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio。 如需啟用在伺服器上的 TCP/IP 通訊協定的詳細資訊，請參閱[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md)。  
  
#### <a name="to-deploy-the-assembly-using-visual-studio"></a>使用 Visual Studio 來部署組件  
  
1.  建置專案時選取**建置**\<專案名稱 > 從**建置**功能表。  
  
2.  解決所有建立錯誤和警告，然後再將組件部署至測試伺服器。  
  
3.  選取**部署**從**建置**功能表。 然後，系統就會在第一次於 Visual Studio 中建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 專案時指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體和資料庫中註冊此組件。  
  
#### <a name="to-deploy-the-assembly-using-transact-sql"></a>使用 Transact-SQL 來部署組件  
  
1.  使用 .NET Framework 隨附的命令列編譯器來編譯來源檔案的組件。  
  
2.  若為 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 來源檔案：  
  
3.  `csc /target:library C:\helloworld.cs`  
  
4.  若為 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 來源檔案：  
  
 `vbc /target:library C:\helloworld.vb`  
  
 這些命令會啟動 Visual C# 或 Visual Basic 編譯器使用**/目標**選項來指定要建立的程式庫 DLL。  
  
1.  解決所有建立錯誤和警告，然後再將組件部署至測試伺服器。  
  
2.  在測試伺服器上開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。 建立連接至適當測試資料庫 (例如 AdventureWorks) 的新查詢。  
  
3.  將下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 加入至查詢，藉以在伺服器中建立組件。  
  
 `CREATE ASSEMBLY HelloWorld from 'c:\helloworld.dll' WITH PERMISSION_SET = SAFE;`  
  
1.  然後，您必須在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體中建立程序、函數、彙總、使用者定義型別或觸發程序。 如果**HelloWorld**組件包含名為的方法**HelloWorld**中**程序**類別，下列[!INCLUDE[tsql](../../includes/tsql-md.md)]可以加入至要建立查詢呼叫程序**hello**中[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
 `CREATE PROCEDURE hello`  
  
 `AS`  
  
 `EXTERNAL NAME HelloWorld.Procedures.HelloWorld`  
  
 如需有關建立不同類型的 managed 的資料庫物件中[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，請參閱[clr 使用者定義函數](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)， [clr 使用者定義彙總](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)， [CLR使用者定義型別](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)， [CLR 預存程序](http://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)，和[CLR 觸發程序](http://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)。  
  
## <a name="deploying-the-assembly-to-production-servers"></a>將組件部署至實際伺服器  
 一旦 CLR 資料庫物件已經在測試伺服器上測試並驗證之後，您就可以將它們散發至實際伺服器。 如需有關偵錯 managed 的資料庫物件的詳細資訊，請參閱[偵錯 CLR 資料庫物件](../../relational-databases/clr-integration/debugging-clr-database-objects.md)。  
  
 Managed 資料庫物件的部署作業與一般資料庫物件 (資料表、[!INCLUDE[tsql](../../includes/tsql-md.md)] 常式等項目) 的部署作業很相似。 您可以使用部署指令碼，將包含 CLR 資料庫物件的組件部署至其他伺服器。 您可以使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 的「產生指令碼」功能來建立部署指令碼。 此外，您也可以手動建立部署指令碼，或先使用「產生指令碼」來建立部署指令碼，然後再手動進行更改。 一旦部署指令碼已經建立完成之後，您就可以在其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上執行此指令碼，以便部署 Managed 資料庫物件。  
  
#### <a name="to-generate-a-deployment-script-using-generate-scripts"></a>使用產生指令碼來產生部署指令碼  
  
1.  開啟 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 並連接至已註冊要部署之 Managed 組件或資料庫物件的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。  
  
2.  在**物件總管 中**，依序展開**\<伺服器名稱 >**和**資料庫**樹狀結構。 以滑鼠右鍵按一下 已註冊，請選取 managed 的資料庫物件的所在之資料庫**工作**，然後選取**產生指令碼**。 指令碼精靈隨即開啟。  
  
3.  從清單方塊中選取資料庫，然後按一下**下一步**。  
  
4.  在**選擇指令碼選項**] 窗格中，按一下 [**下一步**，或變更的選項，然後按一下**下一步**。  
  
5.  在**[選擇物件類型**] 窗格中，選擇要部署的資料庫物件的類型。 按一下 **[下一步]**。  
  
6.  在選取每個物件類型**[選擇物件類型**] 窗格中，**選擇\<類型 >**窗格會顯示。 在這個窗格中，您可以從該資料庫物件類型 (已在指定的資料庫中註冊) 的所有執行個體中選擇。 選取一個或多個物件，然後按一下**下一步**。  
  
7.  **輸出選項**窗格時，就全部所需的資料庫物件已選取型別。 選取**指令碼至檔案**並指定指令碼的檔案路徑。 選取 **[下一步]**。 檢閱您的選擇，然後按一下**完成**。 此時，部署指令碼就會儲存至指定的檔案路徑。  
  
## <a name="post-deployment-scripts"></a>部署後指令碼  
 您可以執行部署後指令碼。  
  
 若要加入部署後指令碼，請在您的 Visual Studio 專案目錄中加入稱為 postdeployscript.sql 的檔案。 例如，以滑鼠右鍵按一下您的專案中**方案總管 中**選取**加入現有項目**。 將此檔案加入專案的根目錄中，而非加入 Test Scripts 資料夾中。  
  
 當您按一下 [部署] 時，Visual Studio 就會在專案部署完成之後執行此指令碼。  
  
## <a name="see-also"></a>另請參閱  
 [Common Language Runtime &#40;CLR&#41; 整合程式設計概念](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
