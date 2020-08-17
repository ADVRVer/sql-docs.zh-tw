---
description: 登錄項目 (Visual FoxPro ODBC Driver)
title: " (Visual FoxPro ODBC Driver) 的登錄專案 |Microsoft Docs"
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- registry keys [ODBC]
- Visual FoxPro ODBC driver [ODBC], registry entries
- keys [ODBC]
- FoxPro ODBC driver [ODBC], registry entries
ms.assetid: 1a63d92d-ca3a-46ae-911f-6788292c801e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cc4c5d617590e6435d99756b159c6049551d2d69
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340344"
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>登錄項目 (Visual FoxPro ODBC Driver)
當您安裝 Visual FoxPro ODBC 驅動程式時，安裝程式會在登錄機碼 HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCInst.ini 中更新您系統的登錄，以新增名為 Microsoft Visual FoxPro Driver 的新機碼。 在該索引鍵下，會加入下表所述的值。  
  
|值名稱|值類型|值|  
|----------------|----------------|-----------|  
|APILevel|REG_SZ|「1」|  
|ConnectFunctions|REG_SZ|"YYN"|  
|驅動程式|REG_SZ|vfpodbc.dll 檔案的系統路徑|  
|DriverODBCVer|REG_SZ|"02.50"|  
|FileExtns|REG_SZ|"* .dbf、 \* . cdx、 \* . fpt"|  
|FileUsage|REG_SZ|「1」|  
|安裝程式|REG_SZ|vfpodbc.dll 檔案的系統路徑|  
|SQLLevel|REG_SZ|"0"|  
  
 安裝程式也會將代表預設 Visual FoxPro 驅動程式的「Visual FoxPro 檔案」機碼新增至系統的 HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini 金鑰。 在此機碼下，安裝程式會新增下表所述的值。  
  
|值名稱|值類型|值|  
|----------------|----------------|-----------|  
|驅動程式|REG_SZ|vfpodbc.dll 檔案的系統路徑|  
  
 每次您將 Visual FoxPro ODBC 資料來源新增至 ODBC 設定時，就會針對該資料來源名稱加入新的索引鍵。 資料來源的值會對應至您在 [ **ODBC Visual FoxPro 安裝程式** ] 對話方塊中設定的值，如下表所示。  
  
|值名稱 (關鍵字) |值類型|值|  
|----------------------------|----------------|-----------|  
|自動分頁|REG_SQ|任何支援的排序次序|  
|描述|REG_SZ|資料來源的使用者描述|  
|驅動程式||vfpodbc.dll 檔案的系統路徑|  
|獨佔||[是] 或 [否]|  
|BackgroundFetch||[是] 或 [否]|  
|SourceDB|REG_SZ|的路徑。DBC 檔案|  
|SourceType|REG_SZ|"DBC" 或 "DBF"|  
  
 您不應該直接存取此資訊;當您加入、修改或刪除資料來源時，ODBC 管理員會處理登錄的任何管理。  
  
 您可以使用其中一些關鍵字和值作為 [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) ODBC API 函數中的參數。
