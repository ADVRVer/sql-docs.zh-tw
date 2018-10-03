---
title: CLR 整合程式設計模型限制 |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7c39bb3499302ef1b60744a4332c665506c7fd21
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809036"
---
# <a name="clr-integration-programming-model-restrictions"></a>CLR 整合程式設計模型限制
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  當您要建置受管理的預存程序或其他 managed 的資料庫物件時，有執行的某些程式碼檢查[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，需要考量。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行 managed 程式碼組件上的檢查，它在資料庫中，第一次註冊時使用**CREATE ASSEMBLY**陳述式，也會在執行階段。 也會在執行階段檢查 Managed 程式碼，因為在組件中，可能會有執行階段絕對無法到達的程式碼路徑。  特別是這樣提供了註冊協力廠商組件的彈性，如此一來，當組件中的不安全程式碼設計為在用戶端環境中執行，但是絕對不會在主控的 CLR 內執行時，就不會封鎖該組件。 Managed 程式碼必須符合的需求取決於組件會註冊為**安全**， **EXTERNAL_ACCESS**，或**UNSAFE**，**安全**最嚴格，並如下所示。  
  
 除了對 Managed 程式碼組件所加諸的限制以外，也有授與的程式碼安全性權限。 Common Language Runtime (CLR) 支援稱為 Managed 程式碼之程式碼存取安全性 (CAS) 的安全性模型。 在此模型中，將會根據程式碼的識別來授與權限給組件。 **安全**， **EXTERNAL_ACCESS**，以及**UNSAFE**組件具有不同的 CAS 權限。 如需詳細資訊，請參閱 < [CLR 整合程式碼存取安全性](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)。  
  
## <a name="create-assembly-checks"></a>CREATE ASSEMBLY 檢查  
 當**CREATE ASSEMBLY**陳述式執行時，執行下列檢查每個安全性層級。  如果任何檢查失敗， **CREATE ASSEMBLY**將會失敗並出現錯誤訊息。  
  
### <a name="global-any-security-level"></a>全域 (任何安全性層級)  
 所有參考的組件都必須符合下列其中一個或多個準則：  
  
-   此組件已經在資料庫中註冊。  
  
-   此組件是其中一個支援的組件。 如需詳細資訊，請參閱 <<c0> [ 支援的.NET Framework 程式庫](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)。  
  
-   您正在使用 **CREATE ASSEMBLY FROM * * *\<位置 >，* 所有參考的組件和其相依性也在中找到*\<位置 >*。  
  
-   您正在使用 **CREATE ASSEMBLY FROM * * *\<位元組...>，* ，但所有參考指定空間透過以位元組為單位。  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 所有**EXTERNAL_ACCESS**組件必須符合下列準則：  
  
-   靜態欄位無法用來儲存資訊。 允許唯讀靜態欄位。  
  
-   通過 PEVerify 測試。 用來檢查 MSIL 程式碼及關聯的中繼資料確實符合類型安全需求的 PEVerify 工具 (peverify.exe) 隨附在 .NET Framework SDK 中。  
  
-   同步處理，例如在使用**Contextboundobject**類別中，不會使用。  
  
-   不會使用 Finalizer 方法。  
  
 下列自訂屬性中不允許**EXTERNAL_ACCESS**組件：  
  
-   System.ContextStaticAttribute  
  
-   System.MTAThreadAttribute  
  
-   System.Runtime.CompilerServices.MethodImplAttribute  
  
-   System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
  
-   System.Runtime.Remoting.Contexts.ContextAttribute  
  
-   System.Runtime.Remoting.Contexts.SynchronizationAttribute  
  
-   System.Runtime.InteropServices.DllImportAttribute  
  
-   System.Security.Permissions.CodeAccessSecurityAttribute  
  
-   System.Security.SuppressUnmanagedCodeSecurityAttribute  
  
-   System.Security.UnverifiableCodeAttribute  
  
-   System.STAThreadAttribute  
  
-   System.ThreadStaticAttribute  
  
### <a name="safe"></a>SAFE  
  
-   所有**EXTERNAL_ACCESS**組件條件都會檢查。  
  
## <a name="runtime-checks"></a>執行階段檢查  
 執行階段會檢查程式碼組件是否有下列條件。 如果找到這些條件的任何一個，將不允許執行 Managed 程式碼，而且將會擲回例外狀況。  
  
### <a name="unsafe"></a>UNSAFE  
 載入組件，可以明確地呼叫**System.Reflection.Assembly.Load()** 方法從位元組陣列，或透過使用隱含**Reflection.Emit**命名空間 — 不允許。  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 所有**UNSAFE**條件都會檢查。  
  
 不允許在支援的組件清單中使用下列主機保護屬性 (HPA) 值當做註解的所有類型和方法。  
  
-   SelfAffectingProcessMgmt  
  
-   SelfAffectingThreading  
  
-   Synchronization  
  
-   SharedState  
  
-   ExternalProcessMgmt  
  
-   ExternalThreading  
  
-   SecurityInfrastructure  
  
-   MayLeakOnAbort  
  
-   UI  
  
 如需有關 Hpa 以及一份支援的組件中不允許的類型和成員的詳細資訊，請參閱[主機保護屬性和 CLR 整合程式設計](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)。  
  
### <a name="safe"></a>SAFE  
 所有**EXTERNAL_ACCESS**條件都會檢查。  
  
## <a name="see-also"></a>另請參閱  
 [支援的.NET Framework 程式庫](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)   
 [CLR 整合程式碼存取安全性](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [主機保護屬性和 CLR 整合程式設計](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [建立組件](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
