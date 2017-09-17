---
title: "資料列狀態 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- row status [ODBC]
- cache [ODBC]
ms.assetid: 0f0b1fb6-f697-4ced-811c-2908e210bc71
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8f164b8269e1150cdf7a85e486bcc3fd93a9411f
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="row-status"></a>資料列狀態
> [!IMPORTANT]  
>  將移除這項功能，在未來的版本的 Windows。 避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 Microsoft 建議使用驅動程式的資料指標功能。  
  
 資料指標程式庫建立緩衝區快取中，資料列狀態。 資料指標程式庫會從這個緩衝區擷取資料列狀態陣列 （以 SQL_ATTR_ROW_STATUS_PTR 陳述式屬性指定） 的值。 每個資料列，資料指標程式庫會將這個緩衝區設定為：  
  
-   SQL_ROW_DELETED 便會執行定位時刪除的資料列上的陳述式。  
  
-   遇到與資料來源擷取資料列發生錯誤時的 SQL_ROW_ERROR **SQLFetch**。  
  
-   當它已成功擷取的資料列與資料來源的 SQL_ROW_SUCCESS **SQLFetch**。  
  
-   在資料列上執行的定位的 update 陳述式時 SQL_ROW_UPDATED。
