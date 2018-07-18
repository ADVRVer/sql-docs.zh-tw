---
title: 模擬資訊對話方塊 （資料表匯入精靈） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.impersonationinfo.f1
ms.assetid: bee7eee5-0650-41f1-a372-5076ae97a58c
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a5c9d9b49d41d8f9320ff414925bb4532145d16f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245678"
---
# <a name="impersonation-information-dialog-box-table-import-wizard"></a>模擬資訊對話方塊 (資料表匯入精靈)
  使用 **[模擬資訊]** 頁面可指定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 將用來連接資料來源的認證。 如需有關認證模擬的詳細資訊，請參閱 <<c0> [ 模擬&#40;SSAS 表格式&#41;](tabular-models/impersonation-ssas-tabular.md)。</c0>  
  
## <a name="options"></a>選項。  
 **特定的 Windows 使用者名稱和密碼**  
 選取此選項，可讓表格式模型使用指定之 Windows 使用者帳戶的安全性認證。  
  
 **使用者名稱**  
 輸入要使用之使用者帳戶的網域和名稱。 使用下列格式：  
  
 *\<網域名稱 >* ** \\ ** *\<使用者帳戶名稱 >*  
  
 唯有選取 **[使用特定的使用者名稱和密碼]** 之後，才會啟用此選項。  
  
 **密碼**  
 輸入表格式模型所要使用之使用者帳戶的密碼。  
  
 唯有選取 **[使用特定的使用者名稱和密碼]** 之後，才會啟用此選項。  
  
 **服務帳戶**  
 選取此選項，可使用與管理模型之 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服務相關聯的安全性認證。  
  
## <a name="see-also"></a>另請參閱  
 [模擬&#40;SSAS 表格式&#41;](tabular-models/impersonation-ssas-tabular.md)  
  
  
