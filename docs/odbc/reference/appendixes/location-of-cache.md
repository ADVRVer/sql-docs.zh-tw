---
title: 快取的位置 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 240d6162-4da6-4b1f-96c7-f379f4ecb16f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 78e4378e5895e68e8eeb461560faa88ef9cef837
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="location-of-cache"></a>快取的位置
> [!IMPORTANT]  
>  將移除這項功能，在未來的版本的 Windows。 避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 Microsoft 建議使用驅動程式的資料指標功能。  
  
 資料指標程式庫會快取在記憶體中 Windows® 暫存檔案和資料。 這會限制結果集資料指標程式庫可處理只依據可用磁碟空間的大小。 如果資料指標程式庫快取的結尾插入快取的資料會跨區段界限時，會使用暫存檔。 不過，快取的資料會加入上次儲存的區塊快取中的資料取代。 上次儲存資料區塊會儲存在暫存檔。 如果資料指標程式庫終止異常，例如當電源失敗時，它可以讓 Windows 在磁碟上的暫存檔案。 這些具名的 ~ CTT*nnnn*.tmp 而建立在目前的目錄。  
  
> [!NOTE]  
>  如果資料指標程式庫在 Microsoft® WindowsNT®/為 Windows2000 嘗試在目前的目錄上的暫存檔的快取資料的唯讀共用或光碟 （例如 Mfc 程式庫範例），從執行應用程式 SQLSTATEHY000 （一般錯誤-無法建立檔案緩衝區） 會傳回。
