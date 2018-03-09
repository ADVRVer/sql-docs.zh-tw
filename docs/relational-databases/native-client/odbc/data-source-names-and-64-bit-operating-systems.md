---
title: "資料來源名稱和 64 位元作業系統 |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|ODBC
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 773218e7c0e141c57223f73f998c7ba2e612e927
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>資料來源名稱和 64 位元作業系統
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  若要建立並執行應用程式，當做 64 位元作業系統上的 32 位元應用程式，您必須利用 %windir%\SysWOW64\odbcad32.exe，以 ODBC 管理員身分建立 ODBC 資料來源。  
  
## <a name="remarks"></a>備註  
 64 位元的 Windows 作業系統有兩個 odbcad32.exe 檔案：  
  
-   %SystemRoot%\system32\odbcad32.exe 用於建立與維持 64 位元應用程式的資料來源名稱。  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe 用於建立與維持 32 位元應用程式的資料來源名稱，包括在 64 位元作業系統上執行的 32 位元應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Native Client &#40; ODBC &#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
