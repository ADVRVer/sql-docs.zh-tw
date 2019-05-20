---
title: ConfigurationSetting 方法 - GenerateDatabaseCreationScript | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- GenerateDatabaseCreationScript method
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5bcbcf0fde93dbba2e1d664ef7768232355ba5de
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65581043"
---
# <a name="configurationsetting-method---generatedatabasecreationscript"></a>ConfigurationSetting 方法 - GenerateDatabaseCreationScript
  產生可用來建立報表伺服器資料庫的 SQL 指令碼。  
  
## <a name="syntax"></a>語法  
  
```vb  
Public Sub GenerateDatabaseCreationScript(ByVal DatabaseName As String, _  
    ByVal Lcid As Int32, ByVal IsSharePointMode As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseCreationScript(string DatabaseName, Int32 Lcid,   
    Boolean IsSharePointMode, out string Script, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>參數  
 *Databasename*  
 包含要建立之報表伺服器資料庫名稱的字串。  
  
 *Lcid*  
 用於當地語系化角色名稱的值。  
  
 *IsSharePointMode*  
 指出要以原生模式或 SharePoint 模式建立資料庫。  
  
> [!IMPORTANT]  
>  從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]開始，不支援 *IsSharePointMode*=**True** ，因為在 SharePoint 模式中， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 是 SharePoint 共用服務且不受 WMI 提供者控制。 您應該一律將此參數設定為 **False**。  
  
 *指令碼*  
 [out] 包含所產生之 SQL 指令碼的字串。  
  
 *HRESULT*  
 [out] 指出呼叫成功或失敗的值。  
  
## <a name="return-value"></a>傳回值  
 傳回 *HRESULT* ，指出方法呼叫成功或失敗。 值為 0 表示方法呼叫成功。 非零值則表示已發生錯誤。  
  
## <a name="remarks"></a>Remarks  
 這個方法會產生 SQL 指令碼，以便針對目前所連接之報表伺服器的版本建立報表伺服器資料庫。  
  
 在 *DatabaseName* 參數中提供的值必須符合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫命名慣例。  
  
 產生指令碼時，此方法不會檢查資料庫是否存在。  
  
 產生指令碼時，此方法不會檢查報表伺服器資料庫是否存在。  
  
 產生的指令碼支援 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 和 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]。  
  
## <a name="requirements"></a>需求  
 **命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [MSReportServer_ConfigurationSetting 成員](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
