---
title: "SQLGetData （桌面資料庫驅動程式） |Microsoft 文件"
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
- SQLGetData function [ODBC], Desktop Database Drivers
ms.assetid: c9d9a32d-5dc2-4189-9bfb-2b008bc3d6a3
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e091bf31e034eaabb9c87931bc6b128f5bdeba84
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData （桌面資料庫驅動程式）
此函式可以從任何資料行，擷取資料，不論是否有繫結資料行之後，並在其中擷取資料行的順序為何。  
  
> [!NOTE]  
>  \*在 pcbValue **SQLGetData**可能會傳回倍字元為實際可用的繫結至 ANSI 資料超過 Jet 4.0 資料庫超出 510 個字元。 字元值或較少的 510 會傳回實際 cbValue。
