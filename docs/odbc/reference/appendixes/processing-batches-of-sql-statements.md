---
title: 處理 SQL 陳述式的批次 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], batches
- ODBC cursor library [ODBC], statement processing
- cursor library [ODBC], batches
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
- SQL statements [ODBC], batches
- batches [ODBC], processing batches of SQL statements
ms.assetid: 04b93ef9-11de-47a3-8bd8-ba963c42f182
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c77d60ea3ef1412e66c8bf40937b45647e776e98
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62639560"
---
# <a name="processing-batches-of-sql-statements"></a>批次處理 SQL 陳述式
> [!IMPORTANT]  
>  Windows 的未來版本將移除這項功能。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 Microsoft 建議使用驅動程式的資料指標功能。  
  
 資料指標程式庫不支援 SQL 陳述式，包括 SQL_ATTR_PARAMSET_SIZE 陳述式屬性是大於 1 的 SQL 陳述式的批的次。 如果應用程式提交至資料指標程式庫的 SQL 陳述式的批次，則結果為未定義。
