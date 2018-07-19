---
title: 將 URN 轉換成 SQL Server 提供者路徑 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c9b1b8f1-b117-4e87-9704-2170f62c5c8b
caps.latest.revision: 8
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c0f82e3bb4185a29a8a40247da8ef7533b3d281c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224098"
---
# <a name="convert-urns-to-sql-server-provider-paths"></a>將 URN 轉換成 SQL Server 提供者路徑
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理物件模型 (SMO) 會針對它的物件建立統一資源名稱 (URN)。 每個 URN 可唯一識別 SMO 物件，而且可以使用轉換成 SQL Server PowerShell 提供者路徑`Convert-UrnToPath`cmdlet。  
  
## <a name="converting-urns-to-paths"></a>將 URN 轉換成路徑  
 每一個 URN 都有與物件之路徑相同的資訊，但是格式會不同。 例如，以下為資料表的路徑：  
  
 SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address  
  
 以下是相同物件的 URN：  
  
 Server[@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' and @Schema='Person']  
  
 若您已在 PowerShell 指令碼中建立 SMO 物件，則可以參考 `Urn` 屬性以取得物件的 URN，然後使用 `Convert-UrnToPath` 指令程式，將 SMO URN 字串轉換為 Windows PowerShell 路徑。 然後，您可以使用提供者導覽至路徑上的不同位置。  
  
 如果節點名稱包含 Windows PowerShell 路徑名稱不支援的擴充字元，則 `Convert-UrnToPath` 會在其十六進位表示法中編碼這些字元。 例如，"My:Table" 會以 "My%3ATable" 的形式傳回。  
  
 在 Windows PowerShell 中，如需使用 Cmdlet 的範例，請執行：  
  
```  
Get-Help Convert-UrnToPath -Examples  
```  
  
## <a name="see-also"></a>另請參閱  
 [查詢運算式和統一的資源名稱](../powershell/query-expressions-and-uniform-resource-names.md)   
 [SQL Server PowerShell 提供者](../powershell/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../powershell/sql-server-powershell.md)  
  
  
