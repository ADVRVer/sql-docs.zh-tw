---
title: "子封裝的實作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "子封裝"
ms.assetid: ab0c09d7-ce2e-487d-a1ed-a4b5adb6cc01
caps.latest.revision: 40
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# 子封裝的實作
  使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]實作負載平衡時，其他伺服器上會安裝子封裝，以充分利用可用的 CPU 或伺服器時間。 建立及執行子封裝需要下列步驟：  
  
-   設計子封裝。  
  
-   將封裝移到遠端伺服器。  
  
-   在包含執行子封裝之步驟的遠端伺服器上建立 SQL Server Agent 作業。  
  
-   測試及偵錯 SQL Server Agent 作業和子封裝。  
  
 設計子封裝時，封裝的設計並無任何限制，您可以放入任何所需的功能。 但是，如果封裝會存取資料，您必須確定執行封裝的伺服器擁有資料的存取權。  
  
 若要識別執行子封裝的父封裝，請在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，以滑鼠右鍵按一下方案總管中的封裝，然後按一下 [進入點封裝]。  
  
 子封裝設計完成之後，下一個步驟是將子封裝部署在遠端伺服器上。  
  
## 將子封裝移到遠端執行個體  
 有幾種方法可以將封裝移到其他伺服器。 建議的兩種方法為：  
  
-   使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]來匯出封裝。  
  
-   為包含想要部署之封裝的專案建立部署公用程式，然後執行「封裝安裝精靈」，將封裝安裝到檔案系統或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體，以部署封裝。 如需詳細資訊，請參閱[舊版封裝部署 &#40;SSIS&#41;](../../integration-services/packages/legacy-package-deployment-ssis.md)。  
  
 您必須重複部署到想要使用的每一部遠端伺服器。  
  
## 建立 SQL Server Agent 作業  
 將子封裝部署到各種伺服器之後，請在包含子封裝的每一部伺服器上建立一項 SQL Server Agent 作業。 SQL Server Agent 作業包含一個在呼叫作業代理程式時執行子封裝的步驟。 SQL Server Agent 作業不是排程作業；只有在父封裝呼叫這些作業時，它們才會執行子封裝。 傳回給父封裝的作業成功或失敗通知，反映的是 SQL Server Agent 作業的成功或失敗，以及是否已成功呼叫作業，而非子封裝成功與否或其是否已執行。  
  
## 偵錯 SQL Server Agent 作業和子封裝  
 您可以使用下列其中一種方法來建立 SQL Server Agent 作業及其子封裝：  
  
-   按一下 [偵錯] / [啟動但不偵錯]，以便在 SSIS 設計師中執行每個子封裝。  
  
-   使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]執行遠端電腦上的個別 SQL Server Agent 作業，以確定封裝執行無誤。  
  
 如需有關如何為您從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業執行的封裝進行疑難排解，請參閱 [支援知識庫中的](http://support.microsoft.com/kb/918760) 從 SQL Server Agent 作業步驟呼叫 SSIS 封裝時，SSIS 封裝未執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。  
  
 SQL Server Agent 會檢查 Proxy 的子系統存取權，而且每當作業步驟執行時，就會提供 Proxy 的存取權。  
  
 您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中建立 Proxy。  
  
## 相關工作  
  
-   [使用 SQL Server Management Studio 在 SSIS 伺服器上執行封裝](../../integration-services/packages/run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
  