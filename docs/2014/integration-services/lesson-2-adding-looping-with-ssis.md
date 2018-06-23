---
title: 第 2 課： 加入迴圈 |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01f2ed61-1e5a-4ec6-b6a6-2bd070c64077
caps.latest.revision: 31
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 46f67531366ef7ff91e3afcc4b8d55b7cc08635e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36030320"
---
# <a name="lesson-2-adding-looping"></a>第 2 課：加入迴圈
  在[第 1 課： 建立專案和基本封裝](lesson-1-create-a-project-and-basic-package-with-ssis.md)，您建立的封裝，從單個一般檔案來源擷取資料轉換使用查閱轉換的資料，最後將資料載入**FactCurrency**事實資料表的**AdventureWorksDW2012**範例資料庫。  
  
 不過，擷取、轉換和載入 (ETL) 處理序使用單個一般檔案的情況很罕見。 典型的 ETL 處理序會從多個一般檔案來源擷取資料。 從多個來源擷取資料需要反覆的控制流程。 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 最令人期待的功能之一就是可以輕易地在套件中加入反覆運算或迴圈的能力。  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 提供兩種類型的容器來循環使用封裝迴圈：Foreach 迴圈容器和 For 迴圈容器。 Foreach 迴圈容器會使用列舉值來執行迴圈，而 For 迴圈容器通常會使用變數運算式。 這一課使用 Foreach 迴圈容器。  
  
 Foreach 迴圈容器可讓封裝對指定列舉值的每一位成員重複控制流程。 利用 Foreach 迴圈容器，您可以列舉：  
  
-   ADO 記錄集資料列  
  
-   ADO .Net 結構描述資訊  
  
-   檔案和目錄結構  
  
-   系統、封裝和使用者變數  
  
-   包含在變數中的可列舉物件  
  
-   集合中的項目  
  
-   XML 路徑語言 (XPath) 運算式中的節點  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理物件 (SMO)  
  
 在這一課，您將修改在第 1 課建立的簡易 ETL 封裝，以利用 Foreach 迴圈容器的好處。 您也可以將使用者自訂封裝變數設定為讓教學課程封裝反覆運算資料夾的所有一般檔案。 如果您尚未完成上一課，您也可以複製此教學課程所包含之已完成的第 1 課封裝。  
  
 在這一課，您不會修改資料流程，只會修改控制流程。  
  
> [!IMPORTANT]  
>  這個教學課程需要 **AdventureWorksDW2012** 範例資料庫。 如需如何安裝和部署 **AdventureWorksDW2012**的詳細資訊，請參閱 [CodePlex 上的 Reporting Services 產品範例](http://go.microsoft.com/fwlink/p/?LinkID=526910)。  
  
## <a name="lesson-tasks"></a>課程工作  
 這一課包含下列工作：  
  
-   [步驟 1： 複製第 1 課封裝](lesson-2-1-copying-the-lesson-1-package.md)  
  
-   [步驟 2： 加入和設定 Foreach 迴圈容器](lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
-   [步驟 3： 修改一般檔案連接管理員](lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
-   [步驟 4： 測試第 2 課的教學課程封裝](lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>開始課程  
 [步驟 1： 複製第 1 課封裝](lesson-2-1-copying-the-lesson-1-package.md)  
  
## <a name="see-also"></a>另請參閱  
 [For 迴圈容器](control-flow/for-loop-container.md)  
  
  