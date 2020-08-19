---
description: 步驟 4：填入 [詳細資料] 文字方塊
title: 步驟4：填入 [詳細資料] 文字方塊 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: cb4273e2-c907-4a86-a621-3bf110088228
author: rothja
ms.author: jroth
ms.openlocfilehash: 59b074b3e635457f8d96060575d941e26846281d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452780"
---
# <a name="step-4-populate-the-details-text-box"></a>步驟 4：填入 [詳細資料] 文字方塊
若要填入 [詳細資料] 文字方塊，請建立名為 **recFields** 的新副程式，然後插入下列程式碼：  
  
```  
Sub recFields(r As Record, l As ListBox, t As TextBox)  
    Dim f As Field  
    Dim s As Stream  
    Set s = New Stream  
    Dim str As String  
  
    For Each f In r.Fields  
        l.AddItem f.Name & ": " & f.Value  
    Next  
    t.Text = ""  
    If r!RESOURCE_CONTENTCLASS = "text/plain" Then  
        s.Open r, adModeRead, adOpenStreamFromRecord  
        str = s.ReadText(1)  
        s.Position = 0  
        If Asc(Mid(str, 1, 1)) = 63 Then '//63 = "?"  
            s.Charset = "ascii"  
            s.Type = adTypeText  
        End If  
        t.Text = s.ReadText(adReadAll)  
    End If  
End Sub  
```  
  
 此程式碼會填入 `lstDetails` 傳遞給的簡單記錄的欄位和值 `recFields` 。 如果資源是文字檔，則會從資源記錄開啟文字串流。 程式碼會判斷字元集是否為 ASCII，並將資料流程內容複寫到 `txtDetails` 。  
  
## <a name="see-also"></a>另請參閱  
 [網際網路發佈案例](../../../ado/guide/data/internet-publishing-scenario.md)   
 [步驟 3：填入 [欄位] 清單方塊](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
