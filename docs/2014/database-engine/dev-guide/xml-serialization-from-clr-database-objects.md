---
title: 從 CLR 資料庫物件的 XML 序列化 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- serialization
- XML serialization [CLR integration]
- common language runtime [SQL Server], XML serialization
- XmlSerializer class
ms.assetid: ac84339b-9384-4710-bebc-01607864a344
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8b59c013a9a21aaa50465acd5a565eda5c1e0653
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279824"
---
# <a name="xml-serialization-from-clr-database-objects"></a>從 CLR 資料庫物件進行 XML 序列化
  XML 序列化是下列兩種狀況所需的作業：  
  
-   從 Common Language Runtime (CLR) 物件叫用 Web 服務。  
  
-   將使用者定義型別 (UDT) 轉換成 XML。  
  
 叫用 `XmlSerializer` 類別來執行 XML 序列化通常會產生額外的序列化組件，而且此組件會多載進入含有來源組件的專案中。 不過，基於安全性考量，這個多載在 CLR 中已停用。 因此，呼叫 web 服務或執行從 UDT 轉換成 XML 內[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，必須使用名為的工具，以手動方式建立組件**Sgen.exe**提供會產生必要的.NET framework序列化組件。 叫用 `XmlSerializer` 時，您必須遵循下列步驟，手動建立序列化組件：  
  
1.  執行**Sgen.exe**工具隨附於.NET Framework SDK 來建立包含來源組件之 XML 序列化程式的組件。  
  
2.  使用 `CREATE ASSEMBLY` 陳述式，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中註冊已產生的組件。  
  
 如需詳細資訊錯誤，您可能會收到時執行 XML 序列化，下列的 Microsoft 支援服務文章： [「 無法載入以動態方式產生的序列化組件 」](http://support.microsoft.com/kb/913668)。  
  
 如需有關 XMLSerializer 不支援之資料類型的詳細資訊，請參閱 .NET Framework 文件集中的＜.NET Framework 中的 XML 結構描述繫結支援＞。  
  
## <a name="see-also"></a>另請參閱  
 [從 CLR 資料庫物件的資料存取](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)   
 [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
  
