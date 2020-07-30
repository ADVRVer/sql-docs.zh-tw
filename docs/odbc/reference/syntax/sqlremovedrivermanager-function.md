---
title: SQLRemoveDriverManager 函式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDriverManager
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDriverManager
helpviewer_keywords:
- SQLRemoveDriverManager function function [ODBC]
ms.assetid: 3a41511f-6603-4b81-a815-7883874023c4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c94765dfe76bc5a1ef188328a6fe27e96671efb1
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87363131"
---
# <a name="sqlremovedrivermanager-function"></a>SQLRemoveDriverManager 函式
**標準**  
 引進的版本： ODBC 3.0：已在 Windows XP Service Pack 2、Windows Server 2003 Service Pack 1 及更新版本的作業系統中被取代。  
  
 **總結**  
 **SQLRemoveDriverManager**會變更，或從系統資訊中的 Odbcinst.ini 專案中移除 ODBC core 元件的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
  
BOOL SQLRemoveDriverManager(  
     LPDWORD     pdwUsageCount);  
```  
  
## <a name="arguments"></a>引數  
 *pdwUsageCount*  
 輸出在呼叫此函式之後，驅動程式管理員的使用量計數。  
  
## <a name="returns"></a>傳回  
 如果成功，函式會傳回 TRUE，如果失敗，則傳回 FALSE。 如果在呼叫此函式時，系統資訊中沒有任何專案存在，此函數會傳回 FALSE。  
  
## <a name="diagnostics"></a>診斷  
 當**SQLRemoveDriverManager**傳回 FALSE 時，可以藉由呼叫**SQLInstallerError**來取得相關聯的* \* pfErrorCode*值。 下表列出可由**SQLInstallerError**傳回的* \* pfErrorCode*值，並在此函式的內容中說明每一個值。  
  
|*\*pfErrorCode*|錯誤|描述|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般安裝程式錯誤|發生錯誤，但沒有特定的安裝程式錯誤。|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|在登錄中找不到元件|安裝程式無法移除驅動程式管理員資訊，因為它不存在於登錄中，或在登錄中找不到。|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|無法遞增或遞減元件使用量計數|安裝程式無法遞減驅動程式管理員的使用量計數。|  
|ODBC_ERROR_OUT_OF_MEM|記憶體不足|因為記憶體不足，所以安裝程式無法執行函數。|  
  
## <a name="comments"></a>註解  
 **SQLRemoveDriverManager**會補充**SQLInstallDriverManager**函數，並更新系統資訊中的元件使用計數。 此函式只能從安裝應用程式呼叫。  
  
 **SQLRemoveDriverManager**會將核心元件使用計數遞減1。 如果元件使用計數變成0，將會移除專案系統資訊。 [核心元件] 專案位於系統資訊的下列位置中，標題為 "ODBC Core"：  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
> [!CAUTION]  
>  當元件使用計數和檔案使用量計數達到零時，應用程式應該不會實際移除驅動程式管理員檔案。  
  
 **SQLRemoveDriverManager**實際上不會移除任何檔案。 呼叫程式會負責刪除檔案及維護檔案使用計數。 不過，如果元件使用計數和檔案使用量計數都已達到零，則不應該移除驅動程式管理員檔案，因為這些檔案可能是其他未遞增檔案使用計數的應用程式所使用。  
  
 **SQLRemoveDriverManager**是在卸載過程中呼叫。 ODBC core 元件（包括驅動程式管理員、資料指標程式庫、安裝程式、語言程式庫、系統管理員、Thunking 檔等等）會全部卸載。 當您在卸載過程中呼叫**SQLRemoveDriverManager**時，不會移除下列檔案：  

:::row:::
    :::column:::
        ODBC32DLL  
        ODBCCR32.DLL  
        ODBCCU32.DLL  
        ODBCINT.DLL  
        ODBCTRAC.DLL  
        MSVCRT40.DLL  
        ODBCCP32.CPL  
    :::column-end:::
    :::column:::
        ODBCCP32.DLL  
        ODBC16GT.DLL  
        ODBC32GT.DLL  
        DS16GT.DLL  
        DS32GT.DLL  
        ODBCAD32.EXE  
    :::column-end:::
:::row-end:::

 **SQLRemoveDriverManager**也會在升級過程中呼叫。 如果應用程式偵測到它必須執行升級，而且先前已安裝驅動程式，則應該移除該驅動程式，然後重新安裝。  
  
 應該先呼叫**SQLRemoveDriverManager**以遞減元件使用計數。 接著，應呼叫**SQLInstallDriverEx**來遞增元件使用計數。 應用程式安裝程式必須以新的檔案取代舊的核心元件檔案。 檔案使用計數會維持不變，而使用舊版核心元件檔案的其他應用程式現在會使用較新版本的檔案。  
  
## <a name="related-functions"></a>相關函數  
  
|如需下列資訊|請參閱|  
|---------------------------|---------|  
|安裝驅動程式管理員|[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|
