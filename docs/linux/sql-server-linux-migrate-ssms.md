---
title: "匯出和匯入 Linux 上的資料庫 |Microsoft 文件"
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 2210cfc3-c23a-4025-a551-625890d6845f
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 174a686a069e4b68958a33bc881f8183c3a32798
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="export-and-import-a-database-on-linux-with-ssms-or-sqlpackageexe-on-windows"></a>匯出和匯入與 SSMS 或在 Windows 上的 SqlPackage.exe Linux 上的資料庫

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

本主題示範如何使用[SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx)和[SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx)匯出和匯入 SQL Server 2017 RC2 on Linux 上的資料庫。 SSMS 和 SqlPackage.exe 是 Windows 應用程式，因此使用這項技術時可以連線到遠端的 SQL Server 執行個體，在 Linux 上的 Windows 電腦。

您一定要安裝並使用最新版本的 SQL Server Management Studio (SSMS) 中所述[使用 SSMS 連接到 SQL Server on Linux 的 Windows 上](sql-server-linux-develop-use-ssms.md)

> [!NOTE]
> 如果您移轉的資料庫從一個 SQL Server 執行個體之間，建議使用[備份和還原](sql-server-linux-migrate-restore-database.md)。

## <a name="export-a-database-with-ssms"></a>匯出資料庫使用 SSMS

1. 啟動 SSMS 輸入**Microsoft SQL Server Management Studio** windows 搜尋] 方塊中，然後按一下 [桌面應用程式。

    ![Transact-SQL](./media/sql-server-linux-develop-use-ssms/ssms.png) 

2. 連接物件總管 中的來源資料庫。 來源資料庫可以是在內部部署執行 Microsoft SQL Server 中，或在雲端中，在 Linux、 Windows 或 Docker 和 Azure SQL Database 或 Azure SQL 資料倉儲。

3. 在 [物件總管] 中的來源資料庫上按一下滑鼠右鍵，指向**工作**，然後按一下**匯出資料層應用程式...**

4. 在匯出精靈 中，按一下**下一步**，然後在**設定**索引標籤上，設定到本機磁碟的位置或 Azure blob 儲存 BACPAC 檔案匯出。

5. 根據預設，會匯出所有資料庫中的物件。 按一下**進階 索引標籤**並選擇您想要匯出的資料庫物件。

6. 按一下 [下一步]，然後按一下 [完成]。

*。在您選擇的位置成功建立 BACPAC 檔案，您準備好將它匯入到目標資料庫。

## <a name="import-a-database-with-ssms"></a>匯入資料庫，以使用 SSMS

1. 啟動 SSMS 輸入**Microsoft SQL Server Management Studio** windows 搜尋] 方塊中，然後按一下 [桌面應用程式。

    ![Transact-SQL](./media/sql-server-linux-develop-use-ssms/ssms.png) 

2. 連接到您在 [物件總管] 中的目標伺服器。 目標伺服器可以是 Microsoft SQL Server 在內部部署或雲端，在 Linux、 Windows 或 Docker 和 Azure SQL Database 或 Azure SQL 資料倉儲中。

3. 以滑鼠右鍵按一下**資料庫**資料夾中 [物件總管]，然後按一下**匯入資料層應用程式...**

4. 若要建立您的目標伺服器的資料庫，指定 BACPAC 檔案從本機磁碟，或選取的 Azure 儲存體帳戶和容器上傳 BACPAC 檔案。

5. 提供新資料庫的資料庫名稱。 如果您要匯入 Azure SQL Database 上的資料庫，設定版本的 Microsoft Azure SQL Database （服務層）、 最大資料庫大小，以及服務目標 （效能層級）。

6. 按一下**下一步**，然後按一下 **完成**BACPAC 檔案匯入到您的目標伺服器中的新資料庫。

*。在您指定的目標伺服器中建立新的資料庫匯入 BACPAC 檔案。

## <a id="sqlpackage"></a>SqlPackage 命令列選項

也可以使用 SQL Server Data Tools (SSDT) 命令列工具， [SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx)，以匯出和匯入 BACPAC 檔案。

下列範例命令會匯出 BACPAC 檔案：

```bash
SqlPackage.exe /a:Export /ssn:tcp:<your_server> /sdn:<your_database> /su:<username> /sp:<password> /tf:<path_to_bacpac>
```

使用下列命令從匯入資料庫結構描述和使用者資料。BACPAC 檔案：

```bash
SqlPackage.exe /a:Import /tsn:tcp:<your_server> /tdn:<your_database> /tu:<username> /tp:<password> /sf:<path_to_bacpac>

```

## <a name="see-also"></a>另請參閱
如需有關如何使用 SSMS 的詳細資訊，請參閱[使用 SQL Server Management Studio](https://msdn.microsoft.com/library/ms174173.aspx)。 如需有關 SqlPackage.exe 的詳細資訊，請參閱[SqlPackage 參考文件](https://msdn.microsoft.com/library/hh550080.aspx)。

