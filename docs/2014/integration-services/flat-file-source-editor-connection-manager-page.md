---
title: 一般檔案來源編輯器 （連接管理員頁面） |Microsoft 文件
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
- sql12.dts.designer.flatfilesourceadapter.connection.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: 2efd6baa-ed75-4f3f-b667-514024cebdb8
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 72cf4b3ee9dbcedb7a8f917328a0bdb715ba575a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36023592"
---
# <a name="flat-file-source-editor-connection-manager-page"></a>一般檔案來源編輯器 (連接管理員頁面)
  使用 **[一般檔案來源編輯器]** 對話方塊的 **[連接管理員]** 頁面，以選取一般檔案來源將要使用的連接管理員。 一般檔案來源會從文字檔讀取資料，其格式可以是分隔、固定寬度或混合格式。  
  
 一般檔案來源可以使用下列其中一種類型的連接管理員：  
  
-   如果來源為單一的一般檔案，則為「一般檔案」連接管理員。 如需詳細資訊，請參閱 [Flat File Connection Manager](connection-manager/file-connection-manager.md)。  
  
-   如果來源為多個一般檔案，而且資料流程工作位於迴圈容器 (如 For 迴圈容器) 內，則為「多個一般檔案」連接管理員。 在此容器的每一個迴圈上，「一般檔案」來源會從「多個一般檔案」連接管理員提供的下一個檔案名稱中載入資料。 如需詳細資訊，請參閱 [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md)。  
  
 若要深入了解一般檔案來源，請參閱＜ [Flat File Source](data-flow/flat-file-source.md)＞。  
  
## <a name="options"></a>選項。  
 **Flat file connection manager**  
 從清單中選取現有的連線管理員，或按一下 [新增] 建立新的連線管理員。  
  
 **新增**  
 使用 [一般檔案連線管理員編輯器] 對話方塊建立新的連線管理員。  
  
 **將來源的 Null 值保留為資料流程中的 Null 值**  
 指定擷取資料時是否保留 Null 值。 此屬性的預設值為 **false**。 當此值為 `alse` 時，一般檔案來源會以各資料行適當的預設值取代來源資料的 Null 值，例如字串資料行的空白字串和數值資料行的零。  
  
 **預覽**  
 使用 [資料檢視] 對話方塊來預覽結果。 預覽最多可顯示 200 個資料列。  
  
## <a name="see-also"></a>另請參閱  
 [Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [一般檔案來源編輯器&#40;資料行頁面&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md)   
 [一般檔案來源編輯器&#40;錯誤輸出頁面&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md)   
 [一般檔案連線管理員](connection-manager/file-connection-manager.md)  
  
  