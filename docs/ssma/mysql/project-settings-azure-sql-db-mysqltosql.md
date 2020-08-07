---
title: 專案設定 (Azure SQL Database)  (MySQLToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8c06420a-533b-4de0-948d-a0c6b368c544
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 4125f73ec34418261d0308221c448cae1fb06298
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87862309"
---
# <a name="project-settings-azure-sql-database-mysqltosql"></a>專案設定 (Azure SQL Database)  (MySQLToSQL) 
SQL Azure 專案設定可讓您設定要在連接對話方塊中新增的 SQL Azure 資料庫尾碼，同時也允許在 SQL Azure 連線中執行「心跳」機制。  
  
[SQL Azure] 窗格可在 [**專案設定**] 和 [**預設專案設定**] 對話方塊中取得。  
  
-   使用 [專案設定] 對話方塊，即可設定目前專案的配置選項。 若要存取 SQL Azure 設定，請在 [**工具**] 功能表上選取 [**專案設定**]，按一下左窗格底部的 **[一般**]，然後選取 [ **SQL Azure**]。  
  
-   使用 [預設專案設定] 對話方塊，即可設定所有專案的設定選項。 若要存取 SQL Azure 設定，請在 [**工具**] 功能表上選取 [ **DefaultProject 設定**]，將 [遷移專案類型] 選取為 [從**遷移目標版本**的 SQL azure] 下拉，以存取 [sql azure] 窗格中的設定，按一下左窗格底部的 **[一般**]，然後選取 [ **SQL Azure**]。  
  
## <a name="options"></a>選項。  
  
## <a name="connectivity"></a>連接性  
**心跳間隔**  
  
指定時間間隔，以用於讓 SQL Azure 連線以「分鐘：秒」格式保持運作的狀態。  
  
**預設值**： ' 4:45 '  
  
值應該以 ' m:ss ' 格式指定 (例如 ' 4:45 ' 或 ' 0:50 ' ) 。  
  
**SQL Azure 伺服器尾碼**  
  
指定 SQL Azure 伺服器尾碼  
  
**預設值**： ' database.windows.net '。  
  
