---
title: 卸載擴充預存程序 DLL |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 148a94bc0413a7fa2a7320599a612b0dcb09d5a6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207950"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>卸載擴充預存程序 DLL
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 請改用 CLR 整合。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 只要進行呼叫，其中的 dll 函式，請載入擴充預存程序 DLL。 該 DLL 在伺服器關閉或系統管理員使用 DBCC 陳述式來卸載它之前，都會保持載入狀態。 例如，此命令會卸載**xp_hello.dll**，允許系統管理員，以將此檔案的較新版本複製到目錄中，而不需要關閉伺服器：  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>另請參閱  
 [DBCC dllname&#40;免費&#41; &#40;TRANSACT-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dllname-free-transact-sql)  
  
  
