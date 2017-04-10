---
title: "嘗試建立與外部資料來源之間的連接時，發生錯誤。 下列連接無法重新整理：Power Pivot 資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1b951da1-f62d-43d2-b40b-270a4a9ab92c
caps.latest.revision: 7
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# 嘗試建立與外部資料來源之間的連接時，發生錯誤。 下列連接無法重新整理：Power Pivot 資料
  如果您在沒有安裝 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint 的伺服器上查詢 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 資料，就會發生此錯誤。 如果 SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) 服務停止，或者您嘗試從舊版檢視 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 資料，也會發生此錯誤。  
  
## 詳細資料  
  
|||  
|-|-|  
|適用對象|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint|  
|產品版本|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|資料連接失敗。|  
|訊息文字|嘗試建立與外部資料來源之間的連接時，發生錯誤。 下列連接無法重新整理︰ [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 資料|  
  
## 說明  
 當您查詢發行到 SharePoint 之 Excel 活頁簿中的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 資料，而 SharePoint 環境中沒有 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint 伺服器或者 SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) 服務已停止時，Excel Services 即會傳回此錯誤。  
  
 如果查詢引擎無法使用，您在配量或篩選 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 資料時將會發生這個錯誤。  
  
## 使用者動作  
 安裝 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint 或是將 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 活頁簿移到已安裝 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint 的 SharePoint 環境。 如需詳細資訊，請參閱 [Power Pivot for SharePoint 2010 安裝](http://msdn.microsoft.com/zh-tw/8d47dde7-c941-4280-a934-e2fe3f9a938f)。  
  
 如果安裝了該軟體，請確認 SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) 執行個體正在執行。 核取 [管理中心] 內的 [管理伺服器上的服務]。 此外，請檢查 [系統管理工具] 中的 [服務] 主控台應用程式。  
  
 若是在 SQL Server 2008 R2 版 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel 中建立的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 活頁簿，您必須安裝 SQL Server 2008 R2 版的 Analysis Services OLE DB 提供者。 如果安裝了此提供者，但沒有註冊 Microsoft.AnalysisServices.ChannelTransport.dll 檔案，就會發生此錯誤。 如需檔案註冊的詳細資訊，請參閱[在 SharePoint 伺服器上安裝 Analysis Services OLE DB 提供者](http://msdn.microsoft.com/zh-tw/2c62daf9-1f2d-4508-a497-af62360ee859)。  
  
## 請參閱＜  
 [資料連接是使用 Windows 驗證，而且無法委派使用者認證。 下列連接無法重新整理：Power Pivot 資料](../../analysis-services/power-pivot-sharepoint/the data connection user could not be delegated.md)  
  
  