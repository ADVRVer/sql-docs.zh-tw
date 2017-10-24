---
title: "使用 Analysis Services 專案和資料庫開發 |Microsoft 文件"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Analysis Services, projects
ms.assetid: 39cf9166-fa92-40fe-9962-210a52461257
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c46155050b4772414f2f5e0d706cbca7dd1740db
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="work-with-analysis-services-projects-and-databases-in-development"></a>使用 Analysis Services 專案和資料庫開發工作
  您可以在專案模式或線上模式中使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 來開發 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 資料庫。  
  
## <a name="single-developer"></a>單一開發人員  
 只有一位開發人員獨自開發整個 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫及其所有構成物件時，此開發人員在商業智慧方案生命週期期間，隨時都可以在專案模式或線上模式中使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 。 在單一開發人員的情況下，選擇模式並不是特別重要。 將離線專案檔案的維護整合到原始檔控制系統會有許多好處，例如封存和回復； 但是，在單一開發人員的作業模式下，將不會與其他開發人員之間有程式碼變更的溝通問題。  
  
## <a name="multiple-developers"></a>多位開發人員  
 當有多位開發人員同時處理某個商業智慧方案時，如果開發人員不是在具有原始檔控制的專案模式下工作 (如果不是所有情況下，則為大多數情況下)，會發生問題； 原始檔控制可確保兩位開發人員不會同時對相同的物件進行變更。  
  
 例如，假設有一位開發人員正在專案模式下工作，並對選定物件進行變更； 當這位開發人員正在進行這些變更時，假設有另一位開發人員要在線上模式中對已部署的資料庫進行變更， 則當第一位開發人員嘗試部署已經過他修改的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案時，將會發生問題； 也就是說， [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 將會偵測到部署之資料庫內已經有變更的物件，並提示第一位開發人員覆寫整個資料庫，如此會覆寫第二位開發人員所做的變更。 由於 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 沒有方法可以解決 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫執行個體以及即將要被覆寫之專案物件之間的變更問題，所以第一位開發人員所擁有的唯一實際選擇就是捨棄他所做的所有變更，並根據目前的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫版本從新的專案重新開始。  
  
  

