---
title: CLR 整合程式碼存取安全性 |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- UNSAFE assemblies
- permissions [CLR integration]
- common language runtime [SQL Server], security
- SAFE assemblies
- code access security [CLR integration]
- EXTERNAL_ACCESS assemblies
ms.assetid: 2111cfe0-d5e0-43b1-93c3-e994ac0e9729
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 25f802f5c9cb67646903179c9100c7014fe466df
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47802276"
---
# <a name="clr-integration-code-access-security"></a>CLR 整合程式碼存取安全性
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Common Language Runtime (CLR) 支援稱為 Managed 程式碼之程式碼存取安全性的安全性模型。 在此模型中，將會根據程式碼的識別來授與權限給組件。 如需詳細資訊，請參閱 .NET Framework 軟體開發套件中的＜程式碼存取安全性＞一節。  
  
 下列三個不同的位置會定義可決定授與給組件之權限的安全性原則：  
  
-   電腦原則：此原則適用於在已安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之電腦中執行的所有 Managed 程式碼。  
  
-   使用者原則：此原則適用於由處理序主控的 Managed 程式碼。 若為 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，則使用者原則為執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務之 Windows 帳戶所特有。  
  
-   主機原則：此原則由 CLR 的主機 (在此案例中為 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) 所設定，適用於在該主機中執行的 Managed 程式碼。  
  
 CLR 所支援的程式碼存取安全性機制是根據執行階段可以主控完全信任和部分信任程式碼的假設。 受 CLR 程式碼存取安全性的資源通常會需要對應的權限，才能允許存取資源的受管理的應用程式開發介面所包裝。 唯有在呼叫堆疊中所有的呼叫者 (在組件層級) 都具有對應的資源權限時，權限的要求才會被滿足。  
  
 在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 內執行時授與給 Managed 程式碼的程式碼存取安全性權限集合是上述三個原則層級所授與之權限集合的交集。 即使 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 將權限集合授與給在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中載入的組件，使用者及電腦層級原則也會進一步限制指定給使用者程式碼的最終權限集合。  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>SQL Server 主機原則層級權限集合  
 由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 主機原則層級授與組件的程式碼存取安全性權限集合是由建立組件時指定的權限集合所決定。 有三個權限集合：**安全**， **EXTERNAL_ACCESS**並**UNSAFE** (使用指定**PERMISSION_SET** 選項[建立組件&#40;TRANSACT-SQL&#41;](../../../t-sql/statements/create-assembly-transact-sql.md))。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 在主控 CLR 時，會將主機層級的安全性原則層級提供給該 CLR；這項原則是在永遠會實行之兩個原則層級之下的另一個原則層級。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]建立的每一個應用程式網域都會設定此原則。 此原則不適用於當 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 建立 CLR 執行個體時所生效的預設應用程式網域。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 主機層級原則，是系統組件的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 固定原則，以及使用者組件的使用者指定原則的組合。  
  
 CLR 組件及 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 系統組件的固定原則會授與它們完全的信任。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 主機原則之使用者指定的部分是根據指定每個組件之下列其中一個權限值區 (共三種) 的組件擁有者。 如需底下所列之安全性權限的詳細資訊，請參閱 .NET Framework SDK。  
  
### <a name="safe"></a>SAFE  
 僅允許內部計算和本機資料存取。 **安全**是限制最嚴格的權限集合。 使用組件所執行的程式碼**安全**權限無法存取外部系統資源，例如檔案、 網路、 環境變數或登錄。  
  
 **安全**組件具有下列權限和值：  
  
|權限|值/描述|  
|----------------|-----------------------------|  
|**SecurityPermission**|**執行：** 執行 managed 程式碼的權限。|  
|**SqlClientPermission**|**內容連接 = true**，**內容連接 = yes**： 只可以使用內容連線，連接字串只能指定值為"內容連接 = true"或"內容連接 = yes"。<br /><br /> **AllowBlankPassword = false:** 不允許空白密碼。|  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 EXTERNAL_ACCESS 組件具有相同的權限**安全**組件，並附帶存取外部系統資源，例如檔案、 網路、 環境變數和登錄的能力。  
  
 **EXTERNAL_ACCESS**組件也具有下列權限和值：  
  
|權限|值/描述|  
|----------------|-----------------------------|  
|**DistributedTransactionPermission**|**不受限制：** 允許分散式交易。|  
|**DNSPermission**|**不受限制：** 向網域名稱伺服器要求資訊的權限。|  
|**EnvironmentPermission**|**不受限制：** 完整允許存取系統和使用者的環境變數。|  
|**EventLogPermission**|**系統管理員：** 允許下列動作： 建立事件來源、 讀取現有的記錄檔、 刪除事件來源或記錄檔、 回應項目、 清除事件記錄檔、 接聽事件，並存取所有事件記錄檔的集合。|  
|**FileIOPermission**|**不受限制：** 完整存取權的檔案和資料夾允許。|  
|**KeyContainerPermission**|**不受限制：** 完整允許對金鑰容器的存取。|  
|**NetworkInformationPermission**|**存取：** Pinging 允許。|  
|**RegistryPermission**|允許的讀取權限**HKEY_CLASSES_ROOT**， **HKEY_LOCAL_MACHINE**， **HKEY_CURRENT_USER**，**機碼 HKEY_CURRENT_CONFIG**，以及**HKEY_USERS。**|  
|**SecurityPermission**|**判斷提示：** 能夠判斷提示的這段程式碼的所有呼叫端具有必要的權限的作業。<br /><br /> **ControlPrincipal:** 操作之主體物件的能力。<br /><br /> **執行：** 執行 managed 程式碼的權限。<br /><br /> **SerializationFormatter:** 能夠提供序列化服務。|  
|**SmtpPermission**|**存取：** 允許的 SMTP 主機連接埠 25 的傳出連接。|  
|**SocketPermission**|**連接：** 允許的傳輸位址上的傳出連接 （所有連接埠，所有的通訊協定）。|  
|**SqlClientPermission**|**不受限制：** 完整允許存取資料來源。|  
|**StorePermission**|**不受限制：** 完整權限允許的 X.509 憑證存放區。|  
|**WebPermission**|**連接：** 允許的網路資源的傳出連接。|  
  
### <a name="unsafe"></a>UNSAFE  
 UNSAFE 可讓組件無限制存取 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 內外部的資源。 從執行的程式碼**UNSAFE**組件也可以呼叫 unmanaged 程式碼。  
  
 **不安全**組件有**FullTrust**。  
  
> [!IMPORTANT]  
>  **安全**是執行計算和資料管理工作，而不需存取外部資源的組件的建議的權限設定[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。 **EXTERNAL_ACCESS**建議用於存取外部資源的組件[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。 **EXTERNAL_ACCESS**以執行組件預設[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]服務帳戶。 可能**EXTERNAL_ACCESS**能夠明確模擬呼叫端的 Windows 驗證安全性內容的程式碼。 因為預設值是執行身分[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]服務帳戶、 權限來執行**EXTERNAL_ACCESS**只應該提供給受信任的服務帳戶身分執行的登入。 安全性的觀點而言， **EXTERNAL_ACCESS**並**UNSAFE**組件完全相同。 不過， **EXTERNAL_ACCESS**組件提供各種可靠性和健全性的保護，不是處於**UNSAFE**組件。 指定**UNSAFE**允許執行不合法的作業，針對組件中的程式碼[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]處理序空間，並因此可能會危害的強固性和延展性[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。 如需有關建立 CLR 組件中的[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，請參閱 <<c2> [ 管理 CLR 整合組件](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)。  
  
## <a name="accessing-external-resources"></a>存取外部資源  
 如果使用者定義型別 (UDT)、 預存程序或其他型別的建構組件已向**安全**設定權限，則此建構中執行的 managed 程式碼是無法存取外部資源。 不過，如果有任一**EXTERNAL_ACCESS**或**UNSAFE**指定的權限集，而且 managed 程式碼嘗試存取外部資源，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]套用下列規則：  
  
|如果|結果為|  
|--------|----------|  
|執行內容對應至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入。|拒絕存取外部資源的嘗試，並引發安全性例外狀況。|  
|執行內容對應至 Windows 登入，並且執行內容是原始呼叫端。|在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務帳戶的安全性內容下存取外部資源。|  
|呼叫端不是原始呼叫端。|拒絕存取並引發安全性例外狀況。|  
|執行內容會對應至 Windows 登入、執行內容就是原始呼叫端，而且已模擬呼叫端。|存取會使用呼叫端安全性內容，而不是服務帳戶。|  
  
## <a name="permission-set-summary"></a>權限集合摘要  
 下表摘要列出授與權限與限制**安全**， **EXTERNAL_ACCESS**，並**UNSAFE**權限集合。  
  
|||||  
|-|-|-|-|  
||**安全**|**EXTERNAL_ACCESS**|**不安全**|  
|**程式碼存取安全性權限**|僅限 Execute|對外部資源的 Execute + 存取權|不受限制 (包括 P/Invoke)|  
|**程式設計模型限制**|是|是|無限制|  
|**可驗證性需求**|是|是|否|  
|**本機資料存取**|是|是|是|  
|**呼叫原生程式碼的能力**|否|否|是|  
  
## <a name="see-also"></a>另請參閱  
 [CLR 整合安全性](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [主機保護屬性和 CLR 整合程式設計](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [CLR 整合程式設計模型限制](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [CLR 主控環境](../../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)  
  
  
