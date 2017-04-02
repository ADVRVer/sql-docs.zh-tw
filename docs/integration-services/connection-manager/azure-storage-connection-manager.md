---
title: "Azure 儲存體連線管理員 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.afpstorageconn.f1"
  - "sql14.dts.designer.afpstorageconn.f1"
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
caps.latest.revision: 13
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# Azure 儲存體連線管理員
  **Azure 儲存體連線管理員**可讓 SSIS 封裝使用您指定的屬性值連接到 Azure 儲存體帳戶︰儲存體帳戶名稱和帳戶金鑰。  
  
>   [!NOTE] 為了確保 Azure 儲存體連線管理員及使用它的元件 - 也就是 Blob 來源、Blob 目的地、Blob 上傳工作和 Blob 下載工作 - 可同時連接到一般目的儲存體帳戶和 Blob 儲存體帳戶，請務必從[這裡](https://www.microsoft.com/download/details.aspx?id=49492)下載最新版的 Azure Feature Pack。 如需這兩種儲存體帳戶類型的詳細資訊，請參閱 [Microsoft Azure 儲存體簡介](https://azure.microsoft.com/en-us/documentation/articles/storage-introduction/#general-purpose-storage-accounts)。
  
 **Azure 儲存體連線管理員**是適用於 SQL Server 2016 之 Azure SQL Server Integration Services (SSIS) 功能套件的元件。 請在 [這裡](http://go.microsoft.com/fwlink/?LinkID=626967)。  
  
1.  在 [加入 SSIS 連線管理員] 對話方塊中，選取 [AzureStorage]，然後按一下 [加入]。  
  
2.  在 [Azure 儲存體連線管理員編輯器] 對話方塊中，選擇 [使用 Azure 帳戶] 透過網際網路連接至 Azure 儲存體服務，或選擇 [使用本機開發人員帳戶] 連接至 Azure 儲存體模擬器裝載的本機服務。  
  
3.  如已選取 [使用 Azure 帳戶] 選項，請執行下列動作︰  
  
    1.  指定 [儲存體帳戶名稱] 和 [帳戶金鑰] 欄位的值。 這些值會儲存為 SSIS 封裝中的機密資料。  
  
    2.  如果您想要使用 HTTPS 而非 HTTP連接到 Azure 儲存體服務，請選取 [使用 HTTPS]。  
  
4.  按一下 **[確定]** ，關閉對話方塊。  
  
5.  您可以在 [屬性] 視窗中看到您建立的連線管理員屬性。  
  
  