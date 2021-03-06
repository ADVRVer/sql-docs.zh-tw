---
title: 連接至 SQL Server (OracleToSQL) |Microsoft Docs
description: 瞭解如何連接到 SQL Server 以遷移 Oracle 資料庫。 SSMA 會取得並顯示 SQL Server 中的資料庫中繼資料。
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connecting to SQL Server,Synchronizing SQL Server Metadata
ms.assetid: 1b2a8059-1829-4904-a82f-9c06de1e245f
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: c810b85b2e59d02b26ee0b831bbbafe2ede5ba28
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87935031"
---
# <a name="connecting-to-sql-server-oracletosql"></a>連線到 SQL Server (OracleToSQL)
若要將 Oracle 資料庫移轉至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 R2 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014，您必須連接到這些目標實例的任何一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 當您連接時，SSMA 會取得實例中所有資料庫的相關中繼資料 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，並在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中繼資料瀏覽器中顯示資料庫中繼資料。 SSMA 會儲存您所連接之實例的相關資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，但不會儲存密碼。  
  
您的連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會保持作用中，直到您關閉專案為止。 當您重新開啟專案時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如果您想要使用中的伺服器連接，則必須重新連接到。 您可以離線工作，直到您將資料庫物件載入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 並遷移資料為止。  
  
有關實例的中繼資料 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不會自動同步處理。 相反地，若要更新中繼資料瀏覽器中的中繼資料 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，您必須手動更新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中繼資料。 如需詳細資訊，請參閱本主題稍後的「同步處理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中繼資料」一節。  
  
## <a name="required-sql-server-permissions"></a>必要的 SQL Server 許可權  
用來連接的帳戶 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 需要不同的許可權，視帳戶執行的動作而定：  
  
-   若要將 Oracle 物件轉換成 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語法、從更新中繼資料 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，或將轉換的語法儲存至腳本，此帳戶必須具有登入實例的許可權 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
-   若要將資料庫物件載入至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，帳戶必須是   **系統管理員（sysadmin** ）伺服器角色的成員。 這是安裝 CLR 元件的必要項。  
  
-   若要將資料移轉至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，帳戶必須是 **系統管理員（sysadmin** ）伺服器角色的成員。 這是執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式資料移轉套件的必要項。  
  
-   若要執行 SSMA 所產生的程式碼，此帳戶必須具有目標資料庫的**ssma_oracle**架構中，所有使用者定義函數的**Execute**許可權。 這些函式會提供對等的 Oracle 系統函數功能，並由轉換的物件使用。  
  
如果用來連接的帳戶 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是執行所有的遷移工作，則帳戶必須是 **系統管理員（sysadmin** ）伺服器角色的成員。  
  
## <a name="establishing-a-sql-server-connection"></a>建立 SQL Server 連接  
將 Oracle 資料庫物件轉換成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 語法之前，您必須建立與實例的連接，以便 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 遷移 oracle 資料庫。  
  
當您定義連接屬性時，您也會指定要遷移物件和資料的資料庫。 連接至之後，您可以在 Oracle 架構層級自訂此對應 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 如需詳細資訊，請參閱 [將 Oracle 架構對應至 SQL Server 架構 &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-schemas-to-sql-server-schemas-oracletosql.md)。  
  
> [!IMPORTANT]  
> 在您嘗試連接到之前 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請確定的實例正在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，而且可以接受連接。  
  
**若要連接到 SQL Server**  
  
1.  **在 [檔案**] 功能表上，選取 **[連接到 SQL Server]**。  
  
    如果您先前已連線到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，命令名稱將會 **重新連接到 SQL Server**。  
  
2.  在 [連接] 對話方塊中，輸入或選取實例的名稱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
    -   如果您要連接到本機電腦上的預設實例，可以輸入 **localhost** 或點 (**.**) 。  
  
    -   如果您要連接至另一部電腦上的預設實例，請輸入電腦的名稱。  
  
    -   如果您要連接至另一部電腦上的已命名實例，請輸入電腦名稱稱，後面接著反斜線，然後輸入實例名稱，例如 MyServer\MyInstance。  
  
3.  如果您的實例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定為接受非預設通訊埠上的連接，請 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在 [ **伺服器埠** ] 方塊中輸入用於連接的埠號碼。 若是的預設實例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，預設的埠號碼為1433。 若為已命名的實例，SSMA 會嘗試從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 瀏覽器服務取得埠號碼。  
  
4.  在 [ **資料庫** ] 方塊中，輸入目標資料庫的名稱。  
  
    當您重新連接至時，無法使用此選項 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
5.  在 [ **驗證** ] 方塊中，選取要用於連接的驗證類型。 若要使用目前的 Windows 帳戶，請選取 [ **Windows 驗證**]。 若要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入，請選取 [ **SQL Server Authentication**]，然後提供登入名稱和密碼。  
  
6.  若為安全連線，則會新增兩個控制項： [ **加密連接** ] 和 [ **TrustServerCertificate** ] 核取方塊。 只有在選取 [ **加密連接** ] 時，才會顯示 [ **TrustServerCertificate** ] 核取方塊。 核取 [ **加密連接** ] (true) 並取消核取 [ **TrustServerCertificate** ] (false) ，它會驗證 SQL Server SSL 憑證。 驗證伺服器憑證是 SSL 交握的一部分，而且這麼做可以確保伺服器是所要連接的正確伺服器。 為了確保這一點，憑證必須安裝在用戶端上，也必須安裝在伺服器端。  
  
7.  按一下 [ **連接**]。  
  
**版本相容性較高**
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 當建立的遷移專案為2005時，您將能夠連接到2008和2012、2014和 2016 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 當建立的遷移專案為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008，但您無法連接到較低的版本（即2005）時，您將能夠連接到2012和2014和 2016 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 當專案建立的 SQL Server 2012 時，您將能夠連接到2012和2014與2016。  
  
|專案類型與目標伺服器版本的比較|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005<br />  (版本： 6.x) |[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008<br />  (版本： 10. x) |[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 <br /> (版本： 11. x) |[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 <br /> (版本： 12. x) |[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 <br /> (版本： 13. x) |Azure SQL Database|  
|-|-|-|-|-|-|-|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|是|是|是|是|是||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||是|是|是|是||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||是|是|是||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014||||是|是||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016|||||是||
|Azure SQL Database||||||是|
  
> [!IMPORTANT]
> 資料庫物件的轉換是根據專案類型來執行，但不會依據您所連接的版本而執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 在2005專案的情況下 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 即使您已連接到較高版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016) ，還是會根據2005執行轉換。  
  
## <a name="synchronizing-sql-server-metadata"></a>同步處理 SQL Server 中繼資料  
資料庫的相關中繼資料 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不會自動更新。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]當您第一次連接時 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，或上次手動更新中繼資料時，中繼資料瀏覽器中的中繼資料是中繼資料的快照集。 您可以手動更新所有資料庫的中繼資料，或任何單一資料庫或資料庫物件的中繼資料。  
  
**若要同步處理中繼資料**  
  
1.  請確定您已連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
2.  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [中繼資料瀏覽器] 中，選取您要更新的資料庫或資料庫架構旁的核取方塊。  
  
    例如，若要更新所有資料庫的中繼資料，請選取 [ **資料庫**] 旁的方塊。  
  
3.  以滑鼠右鍵按一下 [ **資料庫**] 或個別的資料庫或資料庫架構，然後選取 [ **與資料庫同步處理**]。  
  
## <a name="next-step"></a>後續步驟  
遷移的下一個步驟取決於您的專案需求：  
  
-   若要自訂 Oracle 架構與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫與架構之間的對應，請參閱 [將 Oracle 架構對應至 SQL Server 架構 &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-schemas-to-sql-server-schemas-oracletosql.md)。  
  
-   若要自訂專案的設定選項，請參閱 [&#40;OracleToSQL&#41;設定專案選項 ](../../ssma/oracle/setting-project-options-oracletosql.md)。  
  
-   若要自訂來源和目標資料類型的對應，請參閱將 [Oracle 和 SQL Server 資料類型對應 &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md)。  
  
-   如果您不需要執行上述任何一項工作，您可以將 Oracle 資料庫物件定義轉換成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件定義。 如需詳細資訊，請參閱將 [Oracle 架構轉換 &#40;OracleToSQL&#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md)。  
  
## <a name="see-also"></a>另請參閱  
[將 Oracle 資料庫移轉至 SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
