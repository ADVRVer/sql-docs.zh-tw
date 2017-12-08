---
title: "備份選項 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up databases [Analysis Services]
- databases [Analysis Services], backing up
ms.assetid: 02d33fc9-f3f4-4b85-8b90-449b68625cf7
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c8d6af5bf906e5889f0b974537651f46df6ecd68
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="backup-options"></a>備份選項
  有許多方式可備份 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫，且每一種方式都需要您具有伺服器管理員和資料庫管理員權限。 您可以在 **中開啟** [備份] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]對話方塊，選取適當的選項組態，然後從對話方塊本身執行備份。 或者，您可以使用該檔案中已指定的設定來建立指令碼；然後可以儲存指令碼，並視需要來執行指令碼。  
  
## <a name="backup-and-synchronize"></a>備份和同步處理  
 如果資料庫位於 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的遠端執行個體，您可以使用同步處理功能，將資料庫備份至本機執行個體。 資料庫的開發建置可以此方式移到實際作業環境。 您也可以使用傳統的檔案型備份與還原，來將開發建置移到實際作業環境，但同步處理可提供更多的功能。 例如，在開發電腦和實際作業電腦上，您可以有不同的安全性設定；同步處理會提供維護這些設定的選項，並同步處理角色以外的所有物件。 此外，同步處理通常會執行累加更新，來更新來源電腦和目的地電腦不同的物件。 使用備份/還原功能無法進行累加備份。 如需詳細資訊，請參閱 [Synchronize Analysis Services Databases](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)。  
  
> [!IMPORTANT]  
>  Analysis Services 服務帳戶必須擁有針對每個檔案所指定之備份位置的寫入權限。 此外，使用者必須具有下列其中一個角色： [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的管理員角色，或在要備份之資料庫上擁有「完整控制權 (管理員)」權限的資料庫角色成員。  
  
## <a name="see-also"></a>請參閱＜  
 [備份資料庫對話方塊 &#40;Analysis Services - 多維度資料&#41;](http://msdn.microsoft.com/library/7811ce7d-6c37-4189-bfa6-ef36fb4932db)   
 [備份與還原 Analysis Services 資料庫](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)   
 [Backup 元素 &#40;XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)   
 [備份、還原和同步處理資料庫 &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
