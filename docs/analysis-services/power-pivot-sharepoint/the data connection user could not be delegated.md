---
title: "資料連接是使用 Windows 驗證，而且無法委派使用者認證。 下列連接無法重新整理：Power Pivot 資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: d2006df1-d244-4786-b272-49d8996cc88c
caps.latest.revision: 7
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# 資料連接是使用 Windows 驗證，而且無法委派使用者認證。 下列連接無法重新整理：Power Pivot 資料
  如果是包含 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 資料的 Excel 活頁簿，Excel Services 會在無法連接到 SharePoint 中的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 伺服器執行個體時傳回這個錯誤。  
  
## 詳細資料  
  
|||  
|-|-|  
|適用對象|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint|  
|產品版本|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|嘗試使用 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 資料提供者時發生連接失敗。|  
|訊息文字|資料連接是使用 Windows 驗證，而且無法委派使用者認證。 下列連接無法重新整理︰ [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 資料|  
  
## 說明  
 這個錯誤訊息有多個原因。 所有原因背後的共同因素就是 Excel Services 無法從 SharePoint 中的宣告 Token 取得有效的 Windows 使用者識別。 如果是包含 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 資料的 Excel 活頁簿，下列任何條件存在時就會發生這個錯誤：  
  
-   對 Windows Token Service 的宣告未在執行中。 您可以檢視 SharePoint 記錄檔來確認這個錯誤的原因。 如果 SharePoint 記錄檔包含「本機電腦上找不到管線端點 'net.pipe://localhost/s4u/022694f3-9fbd-422b-b4b2-312e25dae2a2'」訊息，就表示對 Windows Token Service 的宣告未在執行中。 若要啟動它，請使用管理中心，然後確認此服務正在服務主控台應用程式中執行。  
  
-   無法使用網域控制站來驗證使用者識別。 對 Windows Token Service 的宣告無法使用快取認證。 它會針對每一個連接來驗證使用者識別。 您可以檢視 SharePoint 記錄檔來確認這個錯誤的原因。 如果 SharePoint 記錄檔包含「無法從 IClaimsIdentity 取得 WindowsIdentity」訊息，則表示無法驗證使用者識別。  
  
-   電腦必須是相同網域的成員，或是位於具有雙向信任關係的網域中。  
  
-   您必須使用 Windows 網域使用者帳戶。 帳戶必須具有通用主要名稱 (UPN)。  
  
-   Excel Services 服務帳戶必須具有查詢物件的 Active Directory 權限。  
  
## 使用者動作  
 使用下列指示來檢查對 Windows Token Service 的宣告狀態。  
  
 如需了解所有其他案例，請向網路管理員查詢。  
  
#### 啟用對 Windows Token Service 的宣告  
  
1.  在管理中心的 [系統設定] 中，按一下 **[管理伺服器上的服務]**。  
  
2.  選取 [對 Windows Token 服務的宣告]，然後按一下 [啟動]。  
  
3.  確認該服務也在服務主控台中執行：  
  
    1.  在 [系統管理工具] 中，按一下 [服務]。  
  
    2.  如果對 Windows Token Service 的宣告未在執行中，則啟動它。  
  
## 請參閱＜  
 [設定 Power Pivot 服務帳戶](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md)  
  
  