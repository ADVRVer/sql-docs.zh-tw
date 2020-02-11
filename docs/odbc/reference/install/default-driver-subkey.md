---
title: 預設驅動程式子機碼 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- default subkey [ODBC]
- registry entries for components [ODBC], default subkey
- subkeys [ODBC], default subkey
- drivers subkey [ODBC]
ms.assetid: 9e58b24f-ebfc-4286-a272-0843b4d6f2d5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e82644d3bddab5d4f6fde6f7103bd9731872bab9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094193"
---
# <a name="default-driver-subkey"></a>預設驅動程式子機碼
預設子機碼包含單一值，可描述預設資料來源所使用的驅動程式。 下表顯示此值的格式。  
  
|名稱|資料類型|資料|  
|----------|---------------|----------|  
|**驅動程式**|REG_SZ|*預設驅動程式-描述*|  
  
 *預設驅動程式描述*名稱與描述驅動程式之 ODBC 驅動程式子機碼下的值名稱相同。  
  
 例如，如果預設資料來源使用 SQL Server 驅動程式，則預設子機碼底下的值可能會是：  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  預設子機碼中包含的預設驅動程式可以參考預設的使用者 DSN 或預設系統 DSN。 如果預設的使用者 DSN 和預設系統 DSN 都已建立，則預設的驅動程式是由最後建立的 DSN 決定，因此它可能不是先建立之 DSN 的有效專案。
