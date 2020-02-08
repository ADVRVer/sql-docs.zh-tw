---
title: 什麼是 SQL Server 語言延伸模組？
titleSuffix: ''
description: 語言延伸模組是 SQL Server 的一個功能，用來執行外部程式碼。 在 SQL Server 2019 中，Java 受到支援。 藉由使用擴充性架構，即可在外部程式碼中使用關聯式資料。
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: overview
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 57755782f2907eff25db942600cebc63f09598e0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2020
ms.locfileid: "73658822"
---
# <a name="what-is-sql-server-language-extensions"></a>什麼是 SQL Server 語言延伸模組？
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

語言延伸模組是 SQL Server 的一個功能，用來執行外部程式碼。 關聯式資料可使用[擴充性架構](concepts/extensibility-framework.md)，用於外部程式碼中。

在 SQL Server 2019 中，Java 受到支援。 預設的 Java Runtime 是 Zulu Open JRE。 您也可以使用另一個 Java JRE 或 SDK。

## <a name="what-you-can-do-with-language-extensions"></a>語言延伸模組的用途

語言延伸模組會使用擴充性架構執行外部程式碼。 程式碼執行與核心引擎流程隔離，但與 SQL Server 查詢執行完全整合。 它們可讓您執行資料所在的程式碼，而不必透過網路提取資料。

外部語言是使用 [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql) 定義的。 系統預存程序 [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) 用來當作執行程式碼的介面使用。

語言延伸模組提供多項優點：

+ 資料安全性。 讓外部語言執行更接近資料來源，可以避免浪費或不安全的資料移動。
+ 速度。 資料庫已針對集合型操作進行最佳化。 資料庫的最新創新 (例如記憶體中的資料表) 讓摘要和彙總變得輕而易舉，而且是資料科學的絕佳補充。
+ 簡化部署和整合。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 是許多其他資料管理工作和應用程式的作業中心點。 使用位於資料庫中的資料可以確保 Java 所使用的資料是一致且最新的。

## <a name="how-to-get-started"></a>如何開始使用

### <a name="step-1-install-the-software"></a>步驟 1:安裝軟體

+ [Windows 的 SQL Server 語言延伸模組](install/install-sql-server-language-extensions-on-windows.md)
+ [Linux 的 SQL Server 語言延伸模組](../linux/sql-server-linux-setup-language-extensions.md)

### <a name="step-2-configure-a-development-tool"></a>步驟 2:設定開發工具

開發人員通常會在他們自己的筆記型電腦或開發工作站上撰寫程式碼。 透過 SQL Server 中的語言延伸模組，不需要變更這個程序。 安裝完成之後，您可以在 SQL Server 上執行 Java 程式碼。

+ **使用您慣用的 IDE** 開發 Java 程式碼。

+ **安裝[適用於 Java 的 Microsoft 擴充性 SDK](how-to/extensibility-sdk-java-sql-server.md)** ，在 SQL Server 上執行 Java 程式碼

+ **使用 [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) 或 [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)** ，在 SQL Server 上執行外部程式碼

+ **使用系統預存程序 [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)** ，在 SQL Server 上執行 Java 程式碼。

### <a name="step-3-write-your-first-code"></a>步驟 3：撰寫您的第一個程式碼

從 T-SQL 指令碼中執行 Java 程式碼：

+ [教學課程：使用 Java 的規則運算式](tutorials/search-for-string-using-regular-expressions-in-java.md)

## <a name="limitations"></a>限制

+ 輸入和輸出緩衝區中的值數目不得超過 `MAX_INT (2^31-1)`，因為這是可在 Java 中以陣列配置的元素數目上限。

## <a name="next-steps"></a>後續步驟

+ 安裝 [Windows 的 SQL Server 語言延伸模組](install/install-sql-server-language-extensions-on-windows.md)或 [Linux 的 SQL Server 語言延伸模組](../linux/sql-server-linux-setup-language-extensions.md)
+ 安裝[適用於 Java 的 Microsoft 擴充性 SDK](how-to/extensibility-sdk-java-sql-server.md)
