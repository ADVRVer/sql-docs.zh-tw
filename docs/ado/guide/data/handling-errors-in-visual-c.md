---
title: Visual c + + 中的錯誤處理 |Microsoft 文件
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- errors [ADO], Visual C++
- Visual C++ error handling [ADO]
ms.assetid: b7576f07-020a-45f7-9e79-b5756f33f7ab
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 68ce5fb8cc94b130de5171a45b65743e86eec3da
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271687"
---
# <a name="handling-errors-in-visual-c"></a>Visual c + + 中的錯誤處理
在 COM 中，大部分的作業會傳回 HRESULT 傳回碼指出函數是否已順利完成。 #Import 指示詞會產生包裝函式程式碼，每個 「 原始 」 的方法或屬性，並檢查傳回的 HRESULT。 如果 HRESULT 指出失敗，包裝函式程式碼會擲回 COM 錯誤的 HRESULT 傳回碼的呼叫 _com_issue_errorex() 做為引數。 可以攔截 COM 錯誤物件，於**try catch**區塊。 （如效率的因素，攔截 _com_error 物件的參考）。  
  
 請記住，這些是 ADO 錯誤： 它們會從 ADO 作業失敗。 基礎提供者所傳回的錯誤會顯示為**錯誤**中的物件**連接**物件的**錯誤**集合。  
  
 #Import 指示詞只會建立錯誤處理常式方法和 ADO.dll 中宣告的屬性。 不過，您可以利用此相同的錯誤處理機制撰寫您自己的錯誤檢查巨集或內嵌函式。 請參閱範例主題 C++® 擴充功能。
