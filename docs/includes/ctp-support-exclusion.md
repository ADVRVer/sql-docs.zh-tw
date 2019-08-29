---
ms.openlocfilehash: ffd608faf64818a7acd9e38d9c502f575be6716a
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653040"
---
## <a name="enabled-deployment-scenarios"></a>已啟用部署案例

SQL Server 2019 候選版 (RC) 可實現下列情節：

- 並存安裝。 安裝 SQL Server 2019 RC 執行個體，以及 SQL Server 2012 到 SQL Server 2017 的執行個體，或是 SQL Server 2019 CTP 3.0 或更高版本的其他執行個體。
   >[!NOTE]
   >雖然 SQL Server 2008 和 2008 R2 不會禁止並存安裝，但它們與 SQL Server 2019 之間並沒有一般支援的 Windows 作業系統版本。
- 就地升級。 從 SQL Server 2012 到 SQL Server 2017 和 SQL Server CTP 3.0 的執行個體，升級至 SQL Server 2019 RC 的執行個體。 不支援從 3.0 以下的 SQL Server 2019 CTP 進行升級，必須執行新的安裝。
   >[!NOTE]
   >雖然不會禁止從 SQL Server 2008 和 2008 R2 進行就地升級，但它們與 SQL Server 2019 之間並沒有一般支援的 Windows 作業系統版本。

## <a name="support"></a>支援

SQL Server 2019 RC 是預覽版軟體。 這不是公開支援運作的軟體。 參與 [SQL 早期採用者計劃](http://aka.ms/sqleap)的客戶，可能透過與 Microsoft 協商的特殊合約支援執行 SQL Server 2019 RC。

您可以在下列其中一個位置，找到針對非早期採用方案客戶提供的有限支援：

- 論壇
  - [SQL Server 使用者入門](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqlgetstarted)
  - [Transact-SQL](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=transactsql)
  - [SQL Server 文件](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqldocumentation)

- 或具有 [#sqlhelp](https://twitter.com/search?q=%23sqlhelp) 的推文 [@SQLServer](https://twitter.com/SQLServer)

**請試用 [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]！**

- [![從評估中心下載](../includes/media/download2.png)](https://go.microsoft.com/fwlink/?LinkID=862101) [下載 [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] 以安裝於 Windows](https://go.microsoft.com/fwlink/?LinkID=862101)。
- 安裝於 Linux for [Red Hat Enterprise Server](../linux/quickstart-install-connect-red-hat.md)、[SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md) 和 [Ubuntu](../linux/quickstart-install-connect-ubuntu.md)。
- [在 Docker 上的 [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] 上執行](../linux/quickstart-install-connect-docker.md)。