---
title: SQLDriverConnect （文字檔驅動程式） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Text File Driver
- text file driver [ODBC], SQLDriverConnect
ms.assetid: d7769021-bd18-4d8e-96e0-e184a82d6ca3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f9343361e7ad6fbfdf68b82218a39a56fa8d928e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053907"
---
# <a name="sqldriverconnect-text-file-driver"></a>SQLDriverConnect (文字檔驅動程式)
> [!NOTE]  
>  本主題提供文字檔驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC API 參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 **SQLDriverConnect**可讓您連接至驅動程式，而不需建立資料來源 (DSN)。  
  
 中的所有驅動程式的連接字串，可支援下列關鍵字：**DSN**， **DBQ**，以及**FIL**。  
  
 下表顯示最小的關鍵字，才能連接到每個驅動程式，並提供搭配使用的關鍵字/值組的範例**SQLDriverConnect**。 如 DRIVERID 值的完整清單，請參閱 < [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)。  
  
> [!NOTE]  
>  如果未指定文字驅動程式的 DBQ 或 DefaultDir，驅動程式會連接到目前的目錄中。  
  
|驅動程式|所需的關鍵字|範例|  
|------------|-----------------------|--------------|  
|Text|驅動程式|Driver={Microsoft Text Driver (*.txt;\*.csv)}; DefaultDir=c:\temp|
