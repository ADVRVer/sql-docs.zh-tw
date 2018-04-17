---
title: 32 位元驅動程式搭配使用 32 位元應用程式 |Microsoft 文件
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
ms.topic: article
helpviewer_keywords:
- ODBC drivers [ODBC], 32-bit applications
- 32-bit applications with 32-bit drivers [ODBC]
ms.assetid: 0cdd5788-5642-4280-8d53-b4ec461aafa1
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 008f948580057fdaa6e59802fd6fa8395140b735
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="using-32-bit-applications-with-32-bit-drivers"></a>32 位元應用程式使用 32 位元驅動程式
您可以使用 32 位元驅動程式來執行 32 位元應用程式。 32 位元應用程式和 32 位元驅動程式會使用 Win32® 應用程式開發介面。  
  
## <a name="architecture"></a>Architecture  
 下圖顯示如何為 32 位元應用程式與 32 位元驅動程式通訊。 應用程式會呼叫 32 位元驅動程式管理員，也就會呼叫 32 位元驅動程式。  
  
 ![如何 32&#45;32 位元應用程式通訊&#45;位元驅動程式](../../odbc/microsoft/media/sdka6.gif "sdka6")  
  
> [!IMPORTANT]  
>  請勿 WindowsNT/windows 2000 上使用 32 位元 thunk 安裝程式 DLL。 雖然有 32 位元安裝程式 DLL 的檔案名稱相同，它是不同的 DLL。  
  
## <a name="administration"></a>系統管理  
 您可以管理 32 位元驅動程式的資料來源使用 ODBC 資料來源管理員。 若要開啟 ODBC 管理員身分執行 Windows 2000 的電腦上，開啟 Windows 控制台中，按兩下**系統管理工具**，然後按兩下**資料來源 (ODBC)**。 在電腦上執行舊版 Windows 中，名為圖示**32 位元 ODBC**或只是**ODBC**。  
  
## <a name="components"></a>Components  
 ODBC 元件包括執行 32 位元驅動程式以 32 位元應用程式的下列檔案。 這些元件是在 \Redist 目錄中。  
  
|檔案名稱|Description|  
|---------------|-----------------|  
|Odbc32.dll|32 位元驅動程式管理員|  
|Odbccp32.dll|32 位元安裝程式 DLL|  
|Odbcad32.exe|32 位元 ODBC 管理員程式|  
|Odbcinst.hlp|安裝程式說明檔|  
|Msvcrt40.dll|C 執行階段程式庫|
