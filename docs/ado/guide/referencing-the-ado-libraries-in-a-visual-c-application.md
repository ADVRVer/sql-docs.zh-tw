---
title: 參考 ADO 程式庫中的 Visual c + + 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual C++ application[ADO]
- ADO, libraries
ms.assetid: d3ea12ec-bca8-48c3-af57-ce14576108c9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 772dbc55fdeb3b038399a3740be472497666e4da
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51290784"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>在 Visual C++ 應用程式中參考 ADO 程式庫
若要使用 ADO 的最新版本，Visual c + + 應用程式中，使用下列`#import`指示詞：  
  
```cpp
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 若要使用 ADO MD 或 ADOX，您必須匯入*msadomd.dll*或是*msadox.dll*，使用上述語法。  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 若要使用任何舊版 ADO，取代*msado15.dll*上述其中一個下列類型程式庫。  
  
-   *msado27.tlb*，ADO 2.7 的型別程式庫  
  
-   *msado26.tlb*，ADO 2.6 的型別程式庫  
  
-   *msado25.tlb*，ADO 2.5 的型別程式庫  
  
-   *msado21.tlb*，ADO 2.1 的型別程式庫  
  
-   *msado20.tlb*，ADO 2.0 類型程式庫
