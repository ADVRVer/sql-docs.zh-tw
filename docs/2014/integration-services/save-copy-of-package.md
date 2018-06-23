---
title: 儲存封裝的副本 |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.savecopyas.f1
helpviewer_keywords:
- Save Copy of Package dialog box
ms.assetid: 7b44c0d7-d8fa-4491-8836-0899f621d3a8
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b42f6861aadb98d97d1b95f688f9dcb891c01697
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36031454"
---
# <a name="save-copy-of-package"></a>儲存封裝的副本
  使用 **[儲存封裝的副本]** 對話方塊 (可以在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中使用)，即可將 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝的副本從 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 儲存到另一個位置，然後選擇性的修改封裝的保護等級。  
  
## <a name="options"></a>選項。  
 **封裝位置**  
 選取要儲存封裝副本之儲存位置的類型。 下列是可以使用的選項：  
  
 **[SQL Server]**  
  
 **檔案系統**  
  
 **SSIS 封裝存放區**  
  
 **Server**  
 輸入伺服器名稱，或者從清單中選取一個伺服器。 唯有儲存位置是 **[SQL Server]** 或 **[SSIS 封裝存放區]** 時，才能使用此選項。  
  
 **驗證**  
 選取 Windows 驗證或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證。 唯有儲存位置是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]時，才能使用這個選項。  
  
> [!IMPORTANT]  
>  儘可能使用 Windows 驗證。  
  
 **驗證類型**  
 選取驗證類型。  
  
 **使用者名稱**  
 如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，請提供使用者名稱。  
  
 **密碼**  
 如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，請提供密碼。  
  
 **封裝路徑**  
 輸入封裝路徑，或按一下瀏覽按鈕 **(…)** ，並找出要儲存封裝的資料夾。  
  
 **保護等級**  
 按一下瀏覽按鈕 **(…)** 並更新 [封裝保護等級] 對話方塊中的保護等級。 如需詳細資訊，請參閱[封裝與專案保護等級對話方塊](../../2014/integration-services/package-and-project-protection-level-dialog-box.md)。  
  
## <a name="see-also"></a>另請參閱  
 [匯入封裝對話方塊 UI 參考](../../2014/integration-services/import-package-dialog-box-ui-reference.md)   
 [匯出封裝對話方塊 UI 參考](../../2014/integration-services/export-package-dialog-box-ui-reference.md)   
 [儲存套件](save-packages.md)   
 [匯入和匯出封裝&#40;SSIS 服務&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  