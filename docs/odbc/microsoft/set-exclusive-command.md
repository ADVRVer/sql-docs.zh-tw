---
title: "SET 獨佔命令 |Microsoft 文件"
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
- SET EXCLUSIVE command [ODBC]
ms.assetid: d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 830cec1dbb87ae2bc4336d28d6112fd76b4db0ed
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="set-exclusive-command"></a>SET 獨佔命令
指定是否開啟檔案資料表，以取得獨佔或共用網路上使用。  
  
## <a name="syntax"></a>語法  
  
```  
  
SET EXCLUSIVE ON | OFF  
```  
  
## <a name="arguments"></a>引數  
 ON  
 開啟以開啟它的使用者，在網路上的資料表限制存取範圍。 資料表無法存取網路上其他使用者。 SET 獨佔 ON 也會防止所有其他使用者擁有唯讀存取權。  
  
 OFF  
 （預設的驅動程式，Visual FoxPro 的預設值為 ON 的全域資料的工作階段和 OFF 私用資料的工作階段）。可讓您開啟共用及修改任何使用者在網路上的網路上的資料表。  
  
## <a name="remarks"></a>備註  
 變更設定專用的設定不會變更狀態的先前開啟的資料表。 例如，如果資料表已開啟以設定獨佔設為 ON，設定獨佔稍後變更為 OFF，資料表會保留其獨佔使用狀態。  
  
## <a name="see-also"></a>另請參閱  
 [ODBC Visual FoxPro 安裝程式 對話方塊](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)

