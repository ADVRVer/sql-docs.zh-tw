---
title: "SET 唯一命令 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SET UNIQUE command [ODBC]
ms.assetid: 1f69e31e-4599-47cc-ac89-b86fba8703c5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0ba0921d2bfab8911d129ac4d1430e6d8d9bd6fe
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="set-unique-command"></a>SET 唯一命令
指定是否具有重複的索引鍵值的記錄會保存在索引檔案中。  
  
## <a name="syntax"></a>語法  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>引數  
 ON  
 指定在索引檔案，都不包含任何重複的索引鍵值的記錄。 只有原始的索引鍵值的第一個記錄包含在索引檔案。  
  
 OFF  
 （預設值）。指定在索引檔案中包含重複的索引鍵值的記錄。  
  
## <a name="remarks"></a>備註  
 當您發出重新索引時，索引檔案都會保留其設定唯一的設定。 如需詳細資訊，請參閱[索引](../../odbc/microsoft/index-command.md)。
