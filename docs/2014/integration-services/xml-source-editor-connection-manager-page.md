---
title: XML 來源編輯器 （連接管理員頁面） |Microsoft 文件
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
- sql12.dts.designer.xmlsourceadapter.connectionmanager.f1
helpviewer_keywords:
- XML Source Editor
ms.assetid: e6507403-a3ce-4b6f-91fc-a7de9f7b6283
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 48193a85232443ea8a5fbc618582a2503e32f84b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36023803"
---
# <a name="xml-source-editor-connection-manager-page"></a>XML 來源編輯器 (連接管理員頁面)
  使用 **[XML 來源編輯器]** 的 **[連接管理員]** 頁面，來指定 XML 檔案和轉換 XML 資料的 XSD。  
  
 如需有關 XML 來源的詳細資訊，請參閱＜ [XML Source](data-flow/xml-source.md)＞。  
  
## <a name="static-options"></a>靜態選項  
 **資料存取模式**  
 從來源中指定選取資料的方法。  
  
|ReplTest1|描述|  
|-----------|-----------------|  
|XML 檔案位置|從 XML 檔案擷取資料。|  
|來自變數的 XML 檔案|指定變數中的 XML 檔案名稱。<br /><br /> **相關資訊：**[在封裝中使用變數](../../2014/integration-services/use-variables-in-packages.md)|  
|來自變數的 XML 資料|從變數中擷取 XML 資料。|  
  
 **使用內嵌結構描述**  
 指定 XML 來源資料本身是否包含定義及驗證其結構和資料的 XSD 結構描述。  
  
 **XSD 位置**  
 輸入 XSD 結構描述檔案的路徑和檔案名稱，或按一下 [瀏覽] 來找出檔案。  
  
 **瀏覽**  
 使用 [開啟] 對話方塊來找出 XSD 結構描述檔案。  
  
 **產生 XSD**  
 使用 [另存新檔] 對話方塊，來選取自動產生之 XSD 結構描述檔案的位置。 編輯器會從 XML 資料的結構中推斷結構描述。  
  
## <a name="data-access-mode-dynamic-options"></a>資料存取模式動態選項  
  
### <a name="data-access-mode--xml-file-location"></a>資料存取模式 = XML 檔案位置  
 **XML 位置**  
 輸入 XML 資料檔的路徑和檔案名稱，或按一下 [瀏覽] 來找出檔案。  
  
 **瀏覽**  
 使用 [開啟] 對話方塊來找出 XML 資料檔。  
  
### <a name="data-access-mode--xml-file-from-variable"></a>資料存取模式 = 來自變數的 XML 檔案  
 **變數名稱**  
 選取包含 XML 檔案之路徑和檔案名稱的變數。  
  
### <a name="data-access-mode--xml-data-from-variable"></a>資料存取模式 = 來自變數的 XML 資料  
 **變數名稱**  
 選取包含 XML 資料的變數。  
  
## <a name="see-also"></a>另請參閱  
 [Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [XML 來源編輯器&#40;資料行頁面&#41;](../../2014/integration-services/xml-source-editor-columns-page.md)   
 [XML 來源編輯器&#40;錯誤輸出頁面&#41;](../../2014/integration-services/xml-source-editor-error-output-page.md)   
 [使用 XML 來源擷取資料](data-flow/extract-data-by-using-the-xml-source.md)  
  
  