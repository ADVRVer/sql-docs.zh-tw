---
title: "Unicode 驅動程式 |Microsoft 文件"
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
- Unicode [ODBC], drivers
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: 3b4742d5-74fb-4aff-aa21-d83a0064d73d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 52afd6864229173b699df74410349b0cac482c98
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="unicode-drivers"></a>Unicode 驅動程式
驅動程式是否應該是 Unicode 驅動程式或 ANSI 驅動程式完全取決於資料來源的本質。 如果資料來源支援 Unicode 資料，此驅動程式應該是 Unicode 驅動程式。 如果資料來源只支援 ANSI 資料，此驅動程式應保留 ANSI 驅動程式。  
  
 Unicode 驅動程式必須匯出**SQLConnectW**被視為 Unicode 驅動程式透過驅動程式管理員。  
  
 Unicode 驅動程式必須接受 Unicode 函式 (且尾碼為*W*) 及儲存 Unicode 資料。 它也可以接受 ANSI 函式，但並不需要。 (驅動程式管理員未通過具有的 ANSI 函式呼叫*A*尾碼至驅動程式，但將以 ANSI 函式呼叫但沒有後置詞，然後將它驅動程式。)  
  
 Unicode 驅動程式必須能夠以 Unicode 或 ANSI、 傳回結果集，根據應用程式的繫結。 如果應用程式繫結至 SQL_C_CHAR，Unicode 驅動程式必須 SQL_WCHAR 資料轉換成 SQL_CHAR。 驅動程式管理員會對應至 SQL_C_CHAR 的 SQL_C_WCHAR ANSI 驅動程式，但不會針對 Unicode 驅動程式沒有對應。  
  
> [!NOTE]  
>  驅動程式管理員在決定驅動程式類型時，會呼叫**SQLSetConnectAttr** ，並在連接時將 SQL_ATTR_ANSI_APP 屬性。 如果應用程式會使用 ANSI 應用程式開發介面，SQL_ATTR_ANSI_APP 將會設定為 SQL_AA_TRUE，而且如果它使用 Unicode，會設定為 SQL_AA_FALSE 的值。 這個屬性使用，讓驅動程式可以展現不同的應用程式類型為基礎的行為。 直接由應用程式不可設定的屬性，它不受支援**SQLGetConnectAttr**。 如果驅動程式表現 ANSI 和 Unicode 應用程式相同的行為，則會傳回 SQL_ERROR，這個屬性。 如果驅動程式傳回 SQL_SUCCESS，驅動程式管理員會分隔 ANSI 和 Unicode 連接所使用的連接共用時。
