---
title: SET 獨佔命令 |Microsoft 文件
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
ms.topic: conceptual
helpviewer_keywords:
- SET EXCLUSIVE command [ODBC]
ms.assetid: d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d0b3fbe2c4902ef58f5060e695a428d2be8879de
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
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
 [ODBC Visual FoxPro 設定對話方塊](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
