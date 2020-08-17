---
description: SQLTables (Excel 驅動程式)
title: SQLTables (Excel 驅動程式) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLTables
- SQLTables function [ODBC], Excel Driver
ms.assetid: 9410b686-4b5b-4b51-b5ef-f9d2e7a48faa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: acedd48fb48e8f8db844feb1911f044c472006a4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339644"
---
# <a name="sqltables-excel-driver"></a>SQLTables (Excel 驅動程式)
> [!NOTE]  
>  本主題提供 Excel 驅動程式特定的資訊。 如需此函數的一般資訊，請參閱 [ODBC API 參考](../../odbc/reference/syntax/odbc-api-reference.md)下的適當主題。  
  
|引數|註解|  
|--------------|--------------|  
|*szTableOwner*|*SzTableOwner*唯一有效的引數為 Null，因為沒有任何驅動程式支援擁有者名稱。 當 *szTableOwner* 設定為 Null 時，就會傳回所有資料表。 TABLE_OWNER 資料行中會傳回 Null。|  
|*szTableQualifier*|使用 Microsoft Excel 3.0 或4.0 驅動程式時，如果您使用*szTableQualifier*的值（不是現有資料表的名稱）來呼叫**SQLTables** ，驅動程式將會建立具有該名稱的資料表。<br /><br /> 在 TABLE_QUALIFIER 資料行中， **SQLTables** 會傳回目錄的路徑。|  
|*SzTableType*|若為 Microsoft Excel 3.0 或4.0，「資料表」是唯一支援的資料表類型。<br /><br /> 針對較新版本的 Microsoft Excel 檔案，會針對工作表名稱傳回「系統資料表」 (資料表的) 的 "$"，並針對工作表中的資料表傳回 "TABLE"。|
