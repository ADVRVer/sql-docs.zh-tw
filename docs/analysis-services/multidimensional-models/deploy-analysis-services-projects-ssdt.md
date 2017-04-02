---
title: "部署 Analysis Services 專案 (SSDT) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "部署 [Analysis Services]"
  - "專案 [Analysis Services], 部署"
  - "Business Intelligence Development Studio, 部署專案 [Analysis Services]"
ms.assetid: 29490a5b-1573-4a35-9277-10c6a6e4ef0e
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 34
---
# 部署 Analysis Services 專案 (SSDT)
  在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中開發 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]專案的期間，您經常會將此專案部署到開發伺服器，以便建立此專案所定義的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫， 這是測試專案所必須採取的作法；例如，為了要瀏覽 Cube 中的資料格、瀏覽維度成員，或是確認關鍵效能指標 (KPI) 公式。  
  
## 部署專案  
 您可以單獨部署專案，也可以部署方案中的所有專案。 當您部署專案時，會依照順序發生幾件事情。 首先，會建立此專案， 這個步驟會建立定義 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫及其構成物件的輸出檔。 接下來，會驗證目的地伺服器。 最後，會在目的地伺服器上建立目的地資料庫及其物件。 在部署期間，部署引擎會以專案的內容完全取代任何已存在的資料庫，除非此專案在之前的部署期間已經建立這些物件。  
  
 在最初的部署之後，會在 [\<專案名稱>\obj] 資料夾中產生 IncrementalSnapshot.xml 檔。 這個檔案是用來判斷，是否已經在專案外部變更目的地伺服器上的資料庫或資料庫的物件； 如果是，將會出現提示，要求您覆寫目的地資料庫中的所有物件。 如果所有的變更都是在專案內進行，而且此專案已設定累加部署，則只會將變更部署到目的地伺服器。  
  
 專案組態及其相關設定會決定將用來部署此專案的部署屬性； 如果是共用專案，每一位開發人員都可以搭配他們自己的專案組態選項來使用他們自己的組態。 例如，每一位開發人員都可以指定不同的測試伺服器，以便能夠與其他開發人員分開作業。  
  
## 請參閱＜  
 [建立 Analysis Services 專案 &#40;SSDT&#41;](../../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)  
  
  