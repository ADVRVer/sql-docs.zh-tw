---
title: Visual Studio.NET 中建立 Visual C# SMO 專案 |Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2bc775f7f857bffb5a7840d99de00fc546e71d03
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "62943024"
---
# <a name="how-to-create-a-visual-c-smo-project-in-visual-studio-net"></a>如何：在 Visual Studio .NET 中建立 Visual C# SMO 專案
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  本節描述如何建立簡單的 SMO 主控台應用程式。  
  
 此範例會匯入命名空間，讓程式可以參考 SMO 類型。 匯入**代理程式**是選擇性的命名空間。 請在撰寫使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的程式時使用該命名空間。 **常見**命名空間，才能建立安全連線的執行個體[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 **SqlClient**命名空間用來處理 SQL 例外狀況錯誤。  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>在 Visual Studio .NET 中建立 Visual C# SMO 專案  
  
1. 啟動 Visual Studio
  
2. 在 **檔案**功能表上，按一下**新增**，然後**專案**。  [新增專案]  對話方塊隨即出現。   
  
3. 在[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]**已安裝** 窗格中，瀏覽至**範本**\\**Visual C#** \\**Windows**選取**主控台應用程式**。  
  
4. （選擇性）在 **名稱**文字中，輸入新的應用程式的名稱。  

5. 按一下 **確定**載入主控台應用程式範本。  

6. 遵循上的指示[Smo&lt](installing-smo.md)安裝適用於您的專案參考的套件。
  
7. 在 [檢視]  功能表中，按一下 [程式碼]  。
    
8. 在程式碼的命名空間陳述式之前，輸入下列命令**使用**陳述式來限定 SMO 命名空間中的類型：
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
15. SMO 在 Microsoft.SqlServer.Management.Smo 之下具有多個命名空間，例如 Microsoft.SqlServer.Management.Smo.Agent。 需要時才新增命名空間。  
  
16. 您現在可以加入您的 SMO 程式碼。  
  
  
