---
title: "檢視 Integration Services 伺服器上的封裝清單 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: service
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67a992d1-7524-4f4b-b3d8-ebd9e5ea82a8
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7686512a05d243f1802d1dd5b0d27bd777210161
ms.contentlocale: zh-tw
ms.lasthandoff: 08/03/2017

---
# <a name="view-the-list-of-packages-on-the-integration-services-server"></a>檢視 Integration Services 伺服器上的封裝清單
  您可以使用下列兩種方式之一，檢視儲存在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器上的封裝清單。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存取  
 若要檢視儲存在伺服器上的封裝清單，請查詢 [catalog.packages &#40;SSISDB 資料庫&#41;](../../integration-services/system-views/catalog-packages-ssisdb-database.md) 檢視。  
  
 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中  
 若要使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的物件總管檢視儲存在伺服器上的封裝，請依照以下的程序進行。  
  
### <a name="to-view-packages-using-includessmanstudiofullincludesssmanstudiofull-mdmd"></a>若要檢視使用的封裝[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器。 亦即連接到主控 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 資料庫的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 執行個體。  
  
2.  在 [物件總管] 中，展開樹狀目錄以顯示 **[Integration Services 目錄]** 節點。  
  
3.  展開 **[Integration Services 目錄]** 節點以顯示 **[SSISDB]** 節點。  
  
4.  展開 **[SSISDB]** 節點以顯示一個或多個資料夾的清單。 每個資料夾在 **[專案]** 資料夾中都包含一個或多個專案，而且每個專案都在 **[封裝]** 資料夾中包含一個或多個封裝。  
  
  

