---
title: 使用頁面 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- PageSize property [ADO]
- pages [ADO]
- Recordset object [ADO]
- AbsolutePage property [ADO]
- PageCount property [ADO]
ms.assetid: 442b08c5-ccc7-4192-a1cc-22f250867782
author: rothja
ms.author: jroth
ms.openlocfilehash: 6542cb23deef9f10979e3bdb90c0820d84c0f150
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763029"
---
# <a name="using-pages"></a>使用頁面
使用**PageCount**屬性來判斷**記錄集**物件中的資料頁數目。 *頁面*是一組記錄，其大小等於**PageSize**屬性設定。 即使最後一頁不完整，因為記錄數目比**PageSize**值少，因此會計算為**PageCount**值中的額外頁面。 如果**記錄集**物件不支援此屬性，則**PageCount**會是-1，表示**PageCount**為未知深度。  
  
 使用**PageSize**屬性來決定組成邏輯頁面的記錄數目。 建立頁面大小可讓您使用**AbsolutePage**屬性移至特定頁面的第一筆記錄。 當您想要讓使用者逐頁流覽資料、一次查看特定數目的記錄時，這在 Web 服務器案例中很有用。  
  
 您可以隨時設定此屬性，其值將用來計算特定頁面的第一筆記錄位置。  
  
 使用**AbsolutePage**屬性來識別目前記錄所在的頁碼。 同樣地，提供者必須支援適當的功能，才能使用此屬性。  
  
 **AbsolutePage**是以1為基礎，而當目前記錄是記錄**集**內的第一筆記錄時，等於1。 設定此屬性，以移至特定頁面的第一筆記錄。 從**PageCount**屬性取得總頁數。
