---
title: 評量報告 (MySQLToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 5525d989-024c-402d-9e84-faa4721cc5b9
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 362a1a5a79fa61b90ea02382018979a003f54424
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87936142"
---
# <a name="assessment-report-mysqltosql"></a>評定報告 (MySQLToSQL)
[評估報告] 視窗會顯示資料庫物件轉換成語法的結果 [!INCLUDE[tsql](../../includes/tsql-md.md)] ，也可以協助您估計遷移專案的複雜性和成本。  
  
若要存取評量報告，請選取要在來源中繼資料瀏覽器中轉換的物件、以滑鼠右鍵按一下 [**架構**]，然後選取 [**建立報表**]。  
  
## <a name="options"></a>選項。  
  
|||  
|-|-|  
|**字詞**|**[定義]**|  
|**轉換統計資料**|依語句類型顯示轉換統計資料。 在左窗格中選取 [群組] 物件（例如 [架構] 或 [沒有程式碼的物件]）時，就會顯示這個窗格。|  
|**依類別分類的物件**|依類別顯示物件的數目。 只有在左窗格中選取 [群組] 物件（例如 [架構] 或 [沒有程式碼的物件]）時，才會顯示這個窗格。|  
|**統計資料**|顯示所選取物件的轉換統計資料。 只有在左窗格中選取了具有程式碼的個別物件時，才會顯示這個窗格。 您可能必須展開 [**統計資料**]，這會緊接在 [**來源**] 窗格上方，以查看此窗格。|  
|**Source**|顯示所選物件的 MySQL 程式碼，並反白顯示未轉換成的程式碼 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。 只有在左窗格中選取了具有程式碼的個別物件時，才會顯示這個窗格。<br /><br />按一下行號以設定或清除書簽。 使用窗格頂端的按鈕來流覽程式碼。|  
|**Target**|顯示所選取物件的轉換結果 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼，以及未轉換之程式碼的錯誤訊息。 只有在左窗格中選取了具有程式碼的個別物件時，才會顯示這個窗格。<br /><br />按一下行號以設定或清除書簽。 使用窗格頂端的按鈕來流覽程式碼。|  
|**訊息窗格**|顯示建立評量報告時所產生的錯誤、警告和參考用訊息。 訊息會依數位分組。 若要查看造成錯誤的程式碼，請按一下 [**錯誤**]、[**警告**] 或 [**資訊**]，展開訊息的類別，然後按一下訊息。|  
  
