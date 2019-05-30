---
title: Common Language Runtime (CLR) 整合概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/20/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- managed code [SQL Server]
- common language runtime [SQL Server], about CLR integration
- cross-language integration
- integrating CLR [SQL Server]
- .NET Framework [SQL Server], common language runtime
- code access security [CLR integration]
- managed code [SQL Server], CLR integration
ms.assetid: 7be9e644-36a2-48fc-9206-faf59fdff4d7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 69903654faf21a7649ec8b54a269e71a99d559c3
ms.sourcegitcommit: 36c5f28d9fc8d2ddd02deb237937c9968d971926
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66354542"
---
# <a name="common-language-runtime-integration"></a>Common Language Runtime 整合
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 並[Azure SQL Database 受控執行個體](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-index)可讓您實作的某些功能使用做為 SQL Server 的伺服器端 （程序、 函式的模組中使用原生的 common language runtime (CLR) 整合的.Net 語言與觸發程序）。 CLR 提供含有如跨語言整合、程式碼存取安全性、物件存留期間管理，以及偵錯和設定檔作業支援的 Managed 程式碼。 對於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者和應用程式開發人員，CLR 整合意味著您現在可以使用任何 .NET Framework 語言 (包括 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET 和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#) 撰寫預存程序、觸發程序、使用者定義型別、使用者定義函數 (純量和資料表值) 和使用者定義彙總函式。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包含預先安裝的 .NET Framework 版本 4。  

> [!WARNING]
>  CLR 使用 .NET Framework 中的程式碼存取安全性 (CAS)，而這不再作為安全性界限受支援。 使用 `PERMISSION_SET = SAFE` 所建立的 CLR 組件可以存取外部系統資源、呼叫 Unmanaged 程式碼，以及取得系統管理員權限。 從 [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] 開始，引進稱為 `clr strict security` 的 `sp_configure` 選項，來增強 CLR 組件的安全性。 `clr strict security` 會依預設啟用，且將 `SAFE` 與 `EXTERNAL_ACCESS` 組件視作已標記為 `UNSAFE` 一樣。 可以基於回溯相容性停用 `clr strict security` 選項，但不建議這麼做。 Microsoft 建議透過具有已獲授與 master 資料庫中 `UNSAFE ASSEMBLY` 權限之對應登入的憑證或非對稱金鑰簽署所有組件。 如需詳細資訊，請參閱 [CLR 嚴格安全性](../../database-engine/configure-windows/clr-strict-security.md)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員也可以將組件新增至資料庫引擎應該信任的組件清單。 如需詳細資訊，請參閱 [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md)。

## <a name="when-to-use-clr-modules"></a>何時使用 CLR 模組？

CLR 整合可讓您實作複雜的功能，可在.Net Framework 規則運算式，例如程式碼來存取外部資源 （伺服器、 web 服務、 資料庫）、 自訂的加密等等。伺服器端 CLR 整合的優點包括：
  
-   **更好的程式設計模型。** .NET Framework 語言在許多方面比 Transact-SQL 豐富，可提供先前未提供給 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 開發人員的建構與功能。 開發人員也可以運用提供一組廣大類別的 .NET Framework 程式庫功能，可用於快速而有效率地解決程式設計問題。  
  
-   **可增進的安全和安全性。** Managed 程式碼會在 Database Engine 主控的 Common Language Run-time 環境下執行。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會運用此環境提供更安全的替代方式給舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所提供的擴充預存程序。  
  
-   **定義資料類型和彙總函式的能力。** 使用者定義型別和使用者定義彙總是兩個新的 Managed 資料庫物件，它們可以擴充 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的儲存和查詢功能。  
  
-   **透過標準化環境簡化的開發。** [!INCLUDE[msCoName](../../includes/msconame-md.md)]資料庫開發會整合到後續版本的  Visual Studio .NET 開發環境中。 開發人員用來開發與偵錯資料庫物件和指令碼的工具，與他們用來撰寫中介層或用戶層的 .NET Framework 元件和服務的工具是一樣的。  
  
-   **更佳的效能和延展性的可能性。** 在許多情況下，.NET Framework 語言編譯和執行模型會透過 Transact-SQL 提供改善的效能。  
  
 下表列出本節中的主題。  
  
 [CLR 整合的概觀](../../relational-databases/clr-integration/clr-integration-overview.md)  
 描述可以使用 CLR 整合建立的物件種類，並檢閱使用 CLR 整合建立資料庫物件的需求。  
  
 [CLR 整合的新功能](../../relational-databases/clr-integration/clr-integration-what-s-new.md)  
 描述這個版本的新功能。  
  
 [CLR 整合的架構](https://msdn.microsoft.com/library/05e4b872-3d21-46de-b4d5-739b5f2a0cf9)  
 描述 CLR 整合的設計目標。  
  
 [啟用 CLR 整合](../../relational-databases/clr-integration/clr-integration-enabling.md)  
 說明如何啟用 CLR 整合。  
  
## <a name="see-also"></a>另請參閱  
 [安裝.NET Framework](https://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx) ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]只)   
 [CLR 整合的效能](../../relational-databases/clr-integration/clr-integration-architecture-performance.md)  
  
  
