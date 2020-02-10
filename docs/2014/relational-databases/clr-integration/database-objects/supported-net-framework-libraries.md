---
title: 支援的 .NET Framework 程式庫 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c2518404830577839bce3e84c4eac9b76c850cd3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "62873774"
---
# <a name="supported-net-framework-libraries"></a>支援的 .NET Framework 程式庫
  利用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中裝載的 Common Language Runtime (CLR)，您能夠以 Managed 程式碼撰寫預存程序、觸發程序、使用者定義函數、使用者定義型別及使用者定義彙總。 藉由 .NET Framework 類別庫所提供的功能，您可以存取預先建立的類別，這些類別可提供字串操作、進階數學運算、檔案存取、加密等多項功能。 您可以透過任何 Managed 預存程序、使用者定義型別、觸發程序、使用者定義函數或使用者定義彙總來存取這些類別。  
  
> [!NOTE]  
>  如果您在全域組件快取（GAC）中服務或升級不支援的[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]元件，您的。 如果元件同時存在於[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR 整合中，則為。 如果您在 GAC 中服務或升級的組件也已在資料庫中註冊 (包括不受支援的 .NET Framework 組件)，請務必也在您的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫中藉由 `ALTER ASSEMBLY` 陳述式來服務或升級該組件的副本。 如需詳細資訊，請參閱[知識庫文章 949080](https://support.microsoft.com/kb/949080)。  
  
## <a name="supported-libraries"></a>支援的程式庫  
 從開始[!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] ，有一份支援的 .NET Framework 程式庫清單，其已進行測試，以確保它們符合與[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]直接從全域組件快取（GAC）載入它們的互動可靠性和安全性標準。  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的 CLR 整合所支援的程式庫/命名空間是：  
  
-   CustomMarshalers  
  
-   Microsoft.VisualBasic  
  
-   Microsoft.VisualC  
  
-   mscorlib  
  
-   系統  
  
-   System.Configuration  
  
-   System.Data  
  
-   System.Data.OracleClient  
  
-   System.Data.SqlXml  
  
-   System.Deployment  
  
-   System.Security  
  
-   System.Transactions  
  
-   System.Web.Services  
  
-   System.Xml  
  
-   System.Core.dll  
  
-   System.Xml.Linq.dll  
  
## <a name="unsupported-libraries"></a>不支援的程式庫  
 不支援的程式庫仍可以從 Managed 預存程序、觸發程序、使用者定義函數、使用者定義型別和使用者定義彙總加以呼叫。 您必須先使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 陳述式在 `CREATE ASSEMBLY` 資料庫中註冊不支援的程式庫，才能在程式碼中使用該程式庫。 為了確保安全性和可靠性，任何在伺服器上註冊及執行的不支援程式庫都應該經過檢閱和測試。  
  
 例如，`System.DirectoryServices` 命名空間並不受支援。 您必須使用 `UNSAFE` 權限註冊 System.DirectoryServices.dll 組件，才能從程式碼中加以呼叫。 
  `UNSAFE` 權限是必要的，因為 `System.DirectoryServices` 命名空間中的類別並不符合 `SAFE` 或 `EXTERNAL_ACCESS` 的需求。 如需詳細資訊，請參閱[Clr 整合程式設計模型限制](clr-integration-programming-model-restrictions.md)和[clr 整合代碼啟用安全性](../security/clr-integration-code-access-security.md)。  
  
## <a name="see-also"></a>另請參閱  
 [建立元件](../assemblies/creating-an-assembly.md)   
 [CLR 整合代碼啟用安全性](../security/clr-integration-code-access-security.md)   
 [CLR 整合程式設計模型限制](clr-integration-programming-model-restrictions.md)  
  
  
