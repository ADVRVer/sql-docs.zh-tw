---
title: "教學課程： 啟用資料表空間使用方式範例深入了解 widget 中 SQL Operations Studio （預覽） |Microsoft 文件"
description: "本教學課程會示範如何啟用的資料表空間使用方式範例深入了解 widget SQL Operations Studio （預覽） 資料庫儀表板上。"
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: tutorial
author: erickangMSFT
ms.author: erickang
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7c51c7d1804baa490e665d316a08d911038c9f11
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>教學課程： 使用情況下啟用資料表的空間使用方式範例深入了解 widget[!INCLUDE[name-sos](../includes/name-sos-short.md)]

本教學課程會示範如何啟用資料庫儀表板上，提供在摘要檢視的空間使用量的相關資料庫中的所有資料表深入了解 widget。 在此教學課程中，您學到如何：

> [!div class="checklist"]
> * 快速開啟使用內建的深入解析 widget 範例深入了解 widget
> * 檢視資料表空間使用量的詳細資料
> * 篩選資料，以及檢視標籤詳細資料，深入了解圖表上

## <a name="prerequisites"></a>必要條件

本教學課程需要 SQL Server 或 Azure SQL Database *TutorialDB*。 若要建立*TutorialDB*資料庫，請完成下列快速入門的其中一個：

- [連接及查詢 SQL Server 使用[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [連接及查詢使用 Azure SQL Database[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>開啟管理 insight 上[!INCLUDE[name-sos](../includes/name-sos-short.md)]的資料庫儀表板
[!INCLUDE[name-sos](../includes/name-sos-short.md)]具有內建範例小工具來監視資料庫中的資料表所使用的空間。

1. 開啟**使用者設定**按**Ctrl + Shift + P**開啟*命令選擇區*，型別*設定*搜尋方塊中選取**喜好設定： 開啟 使用者設定**。

   ![開啟使用者設定命令](./media/tutorial-table-space-sql-server/open-user-settings.png)

2. 型別*儀表板*中設定搜尋輸入方塊，並找出**dashboard.database.widgets**。

   ![搜尋設定](./media/tutorial-table-space-sql-server/search-settings.png)

3. 若要自訂**dashboard.database.widgets**設定，將鉛筆圖示左邊的滑鼠停留**dashboard.database.widgets**文字、 按一下**編輯** > **複製到設定**。

4. 使用[!INCLUDE[name-sos](../includes/name-sos-short.md)]的深入了解設定 IntelliSense、 設定*名稱*widget 標題， *gridItemConfig* widget 大小，和*widget*選取**資料表空間-db 見解**從下拉式清單，如下列螢幕擷取畫面所示：

   ![深入了解設定](./media/tutorial-table-space-sql-server/insight-table-space.png)

5. 按**Ctrl + S**儲存設定。

6. 以滑鼠右鍵按一下資料庫開啟儀表板**TutorialDB**按一下**管理**。

   ![開啟儀表板](./media/tutorial-table-space-sql-server/insight-open-dashboard.png)

7. 檢視*資料表所使用的空間*下列螢幕擷取畫面所示： 

   ![小工具](./media/tutorial-table-space-sql-server/insight-table-space-result.png)


## <a name="working-with-the-insight-chart"></a>使用深入了解圖表

[!INCLUDE[name-sos](../includes/name-sos-short.md)]深入資訊圖提供篩選和滑鼠停留的詳細資料。 嘗試下列步驟：

1. 按一下，並切換*row_count*圖例在圖表上的。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]顯示和隱藏資料數列，如同您切換開啟或關閉圖例。
    
2. 將滑鼠指標停留在圖表中。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]顯示資料數列標籤以及其值，如下列螢幕擷取畫面所示的詳細資訊。

   ![圖表切換和圖例](./media/tutorial-table-space-sql-server/insight-table-space-toggle.png)


## <a name="next-steps"></a>後續步驟
在此教學課程中，您學會如何：
> [!div class="checklist"]
> * 快速開啟使用內建的深入解析 widget 範例深入了解 widget。
> * 檢視資料表空間使用量的詳細資料。
> * 篩選資料，以及檢視標籤詳細資料，深入了解圖表上

若要深入了解如何建置自訂的見解 widget，完成下一個教學課程：

> [!div class="nextstepaction"]
> [建置自訂的見解 widget](tutorial-build-custom-insight-sql-server.md)。
