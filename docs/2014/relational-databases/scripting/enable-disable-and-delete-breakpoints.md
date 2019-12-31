---
title: 啟用、停用以及刪除中斷點
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 357b5874-273f-43a9-8e30-83872bdea5dc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2242511b34c2fc5e588318362b504358b330a30
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2019
ms.locfileid: "75245141"
---
# <a name="enable-disable-and-delete-breakpoints"></a>啟用、停用以及刪除中斷點
  若要查看和管理所有開啟的中斷點，您可以使用 [**中斷點**] 視窗。 這個視窗可用以檢視中斷點資訊，以及採取刪除、停用或啟用中斷點的這類動作。  
  
## <a name="the-breakpoints-window"></a>中斷點視窗  
 
  **[中斷點]** 視窗會列出一些資訊，例如中斷點所在的程式碼行。 在 **[中斷點]** 視窗中，您也可以刪除、停用和啟用中斷點。 如需有關 **[中斷點]** 視窗的詳細資訊，請參閱＜ [[中斷點] Window](transact-sql-debugger-breakpoints-window.md)＞。  
  
 停用中斷點會讓中斷點無法暫停執行，但是會將定義保留在原處，讓您可以在之後想要啟用中斷點時使用。 刪除中斷點，即會永久刪除中斷點。 您必須切換新的中斷點，以暫停陳述式的執行。  
  
## <a name="to-open-the-breakpoints-window"></a>開啟中斷點視窗  
 **若要開啟中斷點視窗**  
  
 您可以利用下列其中一種方式來開啟 **[中斷點]** 視窗：  
  
-   在 **[偵錯]** 功能表上，按一下 **[視窗]**，然後按一下 **[中斷點]**。  
  
-   在 **[偵錯]** 工具列上，按一下 **[中斷點]** 按鈕。  
  
-   按下 CTRL+ALT+B。  
  
## <a name="to-disable-a-single-breakpoint"></a>停用單一中斷點  
 **停用單一中斷點**  
  
 您可以使用下列其中一種方式以停用單一中斷點：  
  
-   在 [查詢編輯器] 視窗中，以滑鼠右鍵按一下中斷點，然後按一下 [停用中斷點]****。  
  
-   在 [中斷點] 視窗中，清除中斷點左側的核取方塊。  
  
## <a name="to-disable-all-breakpoints"></a>停用所有中斷點  
 **停用所有中斷點**  
  
 您可以使用下列其中一種方式以停用所有中斷點：  
  
-   在 **[偵錯]** 功能表上，按一下 **[停用所有中斷點]**。  
  
-   在 **[中斷點]** 視窗的工具列上，按一下 **[停用所有中斷點]** 按鈕。  
  
## <a name="to-enable-a-single-breakpoint"></a>啟用單一中斷點  
 **若要啟用單一中斷點**  
  
 您可以使用下列其中一種方式以啟用單一中斷點：  
  
-   在 [查詢編輯器] 視窗中，以滑鼠右鍵按一下中斷點，然後按一下 [啟用中斷點]****。  
  
-   在 [中斷點] 視窗中，按一下中斷點左側的方塊。  
  
## <a name="to-enable-all-breakpoints"></a>啟用所有中斷點  
 **啟用所有中斷點**  
  
 您可以使用下列其中一種方式以啟用所有中斷點：  
  
-   在 **[偵錯]** 功能表上，按一下 **[啟用所有中斷點]**。  
  
-   在 **[中斷點]** 視窗的工具列上，按一下 **[啟用所有中斷點]** 按鈕。  
  
## <a name="to-delete-a-single-breakpoint"></a>刪除單一中斷點  
 **若要刪除單一中斷點**  
  
 您可以使用下列其中一種方式以刪除單一中斷點：  
  
-   在 [查詢編輯器] 視窗中，以滑鼠右鍵按一下中斷點，然後按一下 [刪除中斷點]****。  
  
-   在 [中斷點] 視窗中，以滑鼠右鍵按一下中斷點，然後按一下捷徑功能表上的 [刪除]****。  
  
-   在 [中斷點] 視窗中，選取中斷點，然後按下 DELETE。  
  
## <a name="to-delete-all-breakpoints"></a>刪除所有中斷點  
 **刪除所有中斷點**  
  
 您可以使用下列其中一種方式以刪除所有中斷點：  
  
-   在 **[偵錯]** 功能表上，按一下 **[刪除所有中斷點]**。  
  
-   在 **[中斷點]** 視窗的工具列上，按一下 **[刪除所有中斷點]** 按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [切換中斷點](../spatial/point.md)  
  
  
