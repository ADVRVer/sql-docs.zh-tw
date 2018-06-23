---
title: 逸出 SQL Server 識別碼 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
caps.latest.revision: 6
author: mgblythe
ms.author: mblythe
manager: jhubbard
ms.openlocfilehash: b11d666165c266467fbdbe46a5d95fb8d7dbad70
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36031664"
---
# <a name="escape-sql-server-identifiers"></a>逸出 SQL Server 識別碼
  您可以經常使用 Windows PowerShell 反勾號逸出字元 (`) 來逸出 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 分隔識別碼中所允許，但是 Windows PowerShell 路徑名稱所不允許的字元。 但是，某些字元無法逸出。 例如，您無法逸出 Windows PowerShell 中的冒號字元 (:)。 具有該字元的識別碼必須加以編碼。 編碼比逸出更為可靠，因為編碼適用於所有字元。  
  
## <a name="before-you-begin"></a>開始之前  
 反勾號字元 (`) 通常是在鍵盤左上方 ESC 鍵底下的按鍵上。  
  
## <a name="examples"></a>範例  
 這是逸出 # 字元的範例：  
  
```  
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```  
  
 這是指定 (local) 做為電腦名稱時的逸出括號範例：  
  
```  
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```  
  
## <a name="see-also"></a>另請參閱  
 [PowerShell 中的 SQL Server 識別碼](sql-server-identifiers-in-powershell.md)   
 [SQL Server PowerShell 提供者](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  