---
title: "Integration Services (SSIS) 伺服器和目錄 |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packages [Integration Services], managing
- managing packages [Integration Services]
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 939f31adf1ab0a975bd4339dabab310ef9025049
ms.contentlocale: zh-tw
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-ssis-server-and-catalog"></a>Integration Services (SSIS) 伺服器和目錄
  在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中設計和測試封裝之後，可以將含有那些封裝的專案部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]伺服器是執行個體[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]裝載**SSISDB**資料庫。 資料庫會儲存封裝、專案、參數、權限、伺服器屬性與作業歷程記錄等物件。  
  
 **SSISDB** 資料庫會透過可供您查詢的公用檢視，公開物件資訊。 此資料庫也會提供預存程序，讓您可加以呼叫來管理物件。  
  
 在您將專案部署至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器之前，必須先建立 **ssDEnoversion** 目錄。  
  
 如需 SSISDB 目錄功能的概觀，請參閱[SSIS 目錄](../../integration-services/service/ssis-catalog.md)。  
  
## <a name="high-availability"></a>高可用性  
 與其他使用者資料庫一樣， **SSISDB** 資料庫也支援資料庫鏡像和複寫。 如需有關鏡像和複寫的詳細資訊，請參閱[資料庫鏡像 &#40;SQL Server &#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 您也可以藉由提供 SSISDB 及其內容的高可用性使用 SSIS 和 Alwayson 可用性群組。 如需詳細資訊，請參閱此部落格文章 Matt masson [SSIS 與 Alwayson](http://go.microsoft.com/fwlink/?LinkId=255873)，blogs.msdn.com 上。  
  
##  <a name="ssms"></a> SQL Server Management Studio 中的 Integration Services Server  
 當您連接到主控 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 資料庫之 **ssDEnoversion** 執行個體時，您會在 [物件總管] 中看到以下物件：  
  
-   **SSISDB 資料庫**  
  
     **SSISDB** 資料庫會出現在 [物件總管] 的 **[資料庫]** 節點下方。 您可以查詢檢視，並呼叫管理 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器和儲存在伺服器上之物件的預存程序。  
  
-   **Integration Services 目錄**  
  
     **[Integration Services 目錄]** 節點下方有 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案和環境的資料夾。  
  
## <a name="related-tasks"></a>相關工作  
  
-   [檢視 Integration Services 伺服器上的封裝清單](../../integration-services/service/view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [部署 Integration Services (SSIS) 專案和封裝](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
-   [執行 Integration Services (SSIS) 套件](../../integration-services/packages/run-integration-services-ssis-packages.md)  
  
## <a name="related-content"></a>相關內容  
 部落格文章： [SSIS 與 Alwayson](http://go.microsoft.com/fwlink/?LinkId=255873)，blogs.msdn.com 上。  
  
  

