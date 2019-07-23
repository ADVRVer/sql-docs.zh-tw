---
title: MSSQLSERVER 屬性的通訊協定 ([進階] 索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 01/24/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: abd5ca68-825f-4c07-b27c-3b3a79d03d74
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: e2cce3ddb17324e234395dcf764855dcffbc44ed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071979"
---
# <a name="protocols-for-mssqlserver-properties-advanced-tab"></a>MSSQLSERVER 的通訊協定內容 (進階索引標籤)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

您可以使用 [MSSQLSERVER 的通訊協定內容]  對話方塊的 [進階]  索引標籤來設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的 [驗證擴充保護]  。 [擴充保護]  是作業系統實作的網路元件功能。 [擴充保護]  可在 Windows 7 和 Windows Server 2008 R2 中使用，而且會包含在舊版作業系統的 Service Pack 中。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在使用 **擴充保護**進行連接時較安全。 [擴充保護]  的某些優點需要在 [旗標]  索引標籤上選取 [強制加密]  。

> [!IMPORTANT]  
> Windows 預設不會啟用 **[擴充保護]** 。 如需有關如何啟用 [**擴充保護**] 的詳細資訊, 請參閱下列各項:
> - [Windows 擴充保護\<extendedProtection\>](https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/windowsauthentication/extendedprotection/)
> - [驗證擴充保護概觀](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/extended-protection-for-authentication-overview) \(機器翻譯\)

如需如何設定其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的詳細資訊及 [擴充保護]  的完整說明，請參閱 [Microsoft.com](https://go.microsoft.com/fwlink/?LinkId=177752) 上最新的資訊。

從 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 開始，[擴充保護]  就受到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 的完整支援。 目前不支援其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端提供者的 [擴充保護]  支援。

## <a name="options"></a>選項。

### <a name="extended-protection"></a>開始就支援

有三個可能的值：  

- **Off**: 表示已停用 [**擴充保護**]。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體將會接受來自任何用戶端的連接，不論用戶端是否受到保護。 **[關閉]** 與舊版及未修補的作業系統相容，但是比較不安全。 只有當您知道用戶端作業系統不支援擴充保護時，才使用這個設定。

- **允許**：表示支援 [擴充保護]  之作業系統的連線便需要 [擴充保護]  。 如果未受保護的用戶端應用程式在受保護的用戶端作業系統上執行，則會拒絕來自該應用程式的連接。 如果未受保護的作業系統發出連接，則會忽略 [擴充保護]  。 這個設定要比 **[關閉]** 安全，但不是最安全的設定。 請在某些作業系統或應用程式支援 [擴充保護]  但某些不支援的混合式環境中使用這個設定。

- **必要**: 表示要接受連線, 它必須來自受保護作業系統上受保護的應用程式。 這個設定是三個選項中最安全的一種。 但不支援 [**擴充保護**] 之作業系統的連接將無法連接到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。

### <a name="accepted-ntlm-spns"></a>接受的 NTLM SPN

的實例[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]可以由一個以上的 NTLM 服務主體名稱 (SPN) 來識別。 您會將 Spn 列為一系列以分號分隔的字串。 例如，**MSSQLSvc/HostName1.Contoso.com;MSSQLSvc/HostName2.Contoso.com** 值表示允許用戶端嘗試連線名為 **MSSQLSvc/HOST1.Contoso.com** 或 **MSSQLSvc/HOST2.Contoso.com** 的 SPN。 此變數的最大長度為 2048,048 個字元。

## <a name="see-also"></a>另請參閱

[含有 Reporting Services 的驗證擴充保護](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)

