---
title: Windows 的隔離變更
description: 本文說明 Windows 上 SQL Server 2019 中機器學習服務的隔離機制變更。 這些變更會影響 SQLRUserGroup、防火牆規則、檔案權限，以及隱含驗證。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4fae460e78682263c604d8e1e86ca40b7b62df97
ms.sourcegitcommit: 187f6d327421e64f1802a3085f88bbdb0c79b707
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69531036"
---
# <a name="sql-server-2019-on-windows-isolation-changes-for-machine-learning-services"></a>Windows 上的 SQL Server 2019：機器學習服務的隔離變更
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

本文說明 Windows 上 SQL Server 2019 中機器學習服務的隔離機制變更。 這些變更會影響 **SQLRUserGroup**、防火牆規則、檔案權限，以及隱含驗證。

如需詳細資訊，請參閱如何[在 Windows 上安裝 SQL Server 機器學習服務](sql-machine-learning-services-windows-install.md)。

## <a name="changes-to-isolation-mechanism"></a>隔離機制的變更

在 Windows 上，SQL Server 2019 安裝程式會變更外部程序的隔離機制。 這項變更會以 [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation) 取代本機背景工作角色帳戶，這是在 Windows 上執行的用戶端應用程式的隔離技術。 

修改後，系統管理員沒有任何特定的動作項目。 在新的或升級的伺服器上，從 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) 執行的所有外部指令碼和程式碼會自動遵循新的隔離模型。 

總結而言，此版本的主要差異如下：

+ **SQL 受限的使用者群組 (SQLRUserGroup)** 下的本機使用者帳戶不再建立或用來執行外部程序。 AppContainers 會取代它們。
+ **SQLRUserGroup** 成員資格已變更。 成員資格只包含 SQL Server Launchpad 服務帳戶，而不是多個本機使用者帳戶。 R 和 Python 程序現在會在透過 AppContainers 隔離的 Launchpad 服務身分識別下執行。

雖然隔離模型已變更，但安裝精靈和命令列參數在 SQL Server 2019 中保持不變。 如需安裝的說明，請參閱[安裝 SQL Server 機器學習服務](sql-machine-learning-services-windows-install.md)。

## <a name="about-appcontainer-isolation"></a>關於 AppContainer 隔離

在舊版中，**SQLRUserGroup** 包含用來隔離和執行外部程序的本機 Windows 使用者帳戶 (MSSQLSERVER00-MSSQLSERVER20) 集區。 當需要外部程序時，SQL Server Launchpad 服務會取得可用的帳戶，並使用它來執行程序。 

在 SQL Server 2019 中，安裝程式不會再建立本機背景工作角色帳戶。 而是透過 [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation) 來完成隔離。 在執行時，當在預存程序或查詢中檢測到內嵌指令碼或程式碼時，SQL Server 會呼叫 Launchpad，並要求特定延伸模組的啟動器。 Launchpad 會在其身分識別的程序中叫用適當的執行時間環境，並具現化 AppContainer 以包含它。 這種變更很有用，因為已不再需要本機帳戶和密碼管理。 此外，在禁止本機使用者帳戶的安裝上，刪除本機使用者帳戶相依性表示您現在可以使用這項功能。

正如 SQL Server 所實作，AppContainers 是一種內部機制。 雖然您不會在程序監視器中看到 AppContainers 的實體辨識項，但是您可以在安裝程式所建立的輸出防火牆規則中找到它們，以避免程序進行網路呼叫。

## <a name="firewall-rules-created-by-setup"></a>安裝程式所建立的防火牆規則

根據預設，SQL Server 會藉由建立防火牆規則來停用輸出連線。 過去，這些規則是以本機使用者帳戶為基礎，其中安裝程式會針對 **SQLRUserGroup** 建立一個輸出規則，該規則拒絕對其成員的網路存取 (每個背景工作角色帳戶都被列為受該規則約束的本機原則)。 

在移至 AppContainers 的過程中，有一些以 AppContainer SID 為基礎的新防火牆規則：SQL Server 安裝程式所建立的 20 個 AppContainers 中的每一個。 防火牆規則名稱的命名慣例是**在 SQL Server 執行個體 MSSQLSERVER 中封鎖 AppContainer-00 的網路存取**，其中 00 是 AppContainer 的數目 (預設為 00-20)，而 MSSQLSERVER 是 SQL Server 執行個體的名稱。 

> [!Note]
> 如果需要網路呼叫，您可以停用 Windows 防火牆中的輸出規則。

## <a name="program-file-permissions"></a>程式檔權限

與以前的版本一樣，**SQLRUserGroup** 繼續提供 SQL Server **Binn**、**R_SERVICES** 和 **PYTHON_SERVICES** 目錄中可執行檔的讀取和執行權限。 在此版本中，**SQLRUserGroup** 的唯一成員是 SQL Server Launchpad 服務帳戶。  當 Launchpad 服務啟動 R 或 Python 執行環境時，程序會以 Launchpad 服務的方式執行。

## <a name="implied-authentication"></a>隱含驗證

如同之前一樣，在指令碼或程式碼必須使用使用受信任的驗證來取出資料或資源的情況下，隱含的驗證  仍需要額外的設定。 額外的設定牽涉到為 **SQLRUserGroup** 建立資料庫登入，其唯一成員現在是單一 SQL Server Launchpad 服務帳戶，而不是多個背景工作角色帳戶。 如需這項工作的詳細資訊，請參閱[將 SQLRUserGroup 新增為資料庫使用者](../security/create-a-login-for-sqlrusergroup.md)。


## <a name="symbolic-link-created-by-setup"></a>安裝程式所建立的符號連結

作為 SQL Server 安裝程式的一部分，將建立到目前預設 **R_SERVICES** 和 **PYTHON_SERVICES** 的符號連結。 如果您不想要建立此連結，替代方法是將「所有應用程式套件」讀取權限授與給資料夾的階層。


## <a name="see-also"></a>另請參閱

+ [在 Windows 上安裝 SQL Server 機器學習服務](sql-machine-learning-services-windows-install.md)
+ [在 Linux 上安裝 SQL Server 機器學習服務](../../linux/sql-server-linux-setup-machine-learning.md)
