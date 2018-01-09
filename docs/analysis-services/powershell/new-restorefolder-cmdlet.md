---
title: "New-restorefolder 指令程式 |Microsoft 文件"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5938b3a9-6412-45fc-86f8-264651d01598
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 20e512bbc1ac3ba7c2a6b6604032c047f83d10cf
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="new-restorefolder-cmdlet"></a>New-RestoreFolder 指令程式
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]將原始資料夾還原到新的資料夾。  

>[!NOTE] 
>這份文件可能包含過時的資訊和範例。 使用 Get-help cmdlet 取得最新。
  
## <a name="syntax"></a>語法  
 `New-RestoreFolder [-OriginalFolder] <String> [-NewFolder] <String> [-AsTemplate] [-Server <String>] [-Credential <PSCredential>] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]`  
  
 `New-RestoreFolder [-Server <String>] [-Credential <PSCredential>] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]`  
  
 一般參數 (例如 -Verbose、-Debug)、錯誤和警告參數、-Whatif 和 -Confirm 都記載於 Windows PowerShell 參考中。 如需詳細資訊，請參閱 [about_CommonParameters](http://technet.microsoft.com/library/dd315352.aspx)。  
  
## <a name="description"></a>描述  
 New-RestoreFolder 指令程式是用來根據原始資料夾的名稱建立新的資料夾。  
  
## <a name="parameters"></a>參數  
  
### <a name="-originalfolder-string"></a>-OriginalFolder\<字串 >  
 取得原始資料夾位置。  
  
|||  
|-|-|  
|必要項？|true|  
|位置？|0|  
|預設值||  
|接受管線輸入？|true|  
|接受萬用字元？|false|  
  
### <a name="-newfolder-string"></a>-NewFolder\<字串 >  
 設定新資料夾的位置。  
  
|||  
|-|-|  
|必要項？|true|  
|位置？|@shouldalert|  
|預設值||  
|接受管線輸入？|true|  
|接受萬用字元？|false|  
  
### <a name="-astemplate-switchparameter"></a>-AsTemplate \<SwitchParameter >  
 指定是否應該在記憶體中建立物件並傳回物件。  
  
|||  
|-|-|  
|必要項？|false|  
|位置？|具名|  
|預設值||  
|接受管線輸入？|false|  
|接受萬用字元？|false|  
  
### <a name="-server-string"></a>伺服器\<字串 >  
 指定指令程式將會連接並執行的 Analysis Services 執行個體。 如果沒有提供伺服器名稱，將會建立 localhost 的連接。 若為預設執行個體，請單獨指定伺服器名稱。 若為具名執行個體，請使用格式 servername\instancename。 若為 HTTP 連接，請使用格式 http[s]://server[:port]/virtualdirectory/msmdpump.dll。  
  
|||  
|-|-|  
|必要項？|false|  
|位置？|具名|  
|預設值|localhost|  
|接受管線輸入？|false|  
|接受萬用字元？|false|  
  
### <a name="-credential-pscredential"></a>-Credential \<PSCredential >  
 若為您已經設定為 HTTP 存取的執行個體，這個參數是在使用 Analysis Service 執行個體的 HTTP 連接時用來傳入使用者名稱和密碼。 如需詳細資訊，請參閱[設定 HTTP 存取 Analysis Services，Internet Information Services &#40; IIS &#41; 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md)進行 HTTP 連線。  
  
 如果指定了此參數，使用者名稱和密碼將會用來連接到指定的 Analysis Server 執行個體。 如果沒有指定認證，則會使用執行此工具之使用者的預設 Windows 帳戶。  
  
 若要使用此參數，請先使用 Get-Credential 來建立 PSCredential 物件，以便指定使用者名稱和密碼 (例如 `$Cred=Get-Credential “adventure-works\bobh”`。 然後，您可以透過管道將這個物件傳送至 -Credential 參數 `(-Credential:$Cred`)。  
  
|||  
|-|-|  
|必要項？|false|  
|位置？|具名|  
|預設值||  
|接受管線輸入？|True (ByValue)|  
|接受萬用字元？|false|  
  
## <a name="inputs-and-outputs"></a>輸入和輸出  
 輸入類型是可透過管道傳送至指令程式的物件類型。 傳回類型是指令程式所傳回的物件類型。  
  
|||  
|-|-|  
|輸入||  
|輸出|無|  
  
